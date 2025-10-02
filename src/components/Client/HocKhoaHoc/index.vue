<template>
  <div class="row mt-4">
    <div v-if="loading" class="col-12 text-center py-5">
      <div class="spinner-border text-primary" role="status"></div>
      <p class="mt-2">Đang tải dữ liệu...</p>
    </div>
    <div v-else-if="error" class="col-12 text-center text-danger py-5">
      {{ error }}
    </div>

    <div v-else class="d-flex flex-wrap">
      <div class="col-lg-4 col-md-12 mb-3">
        <div class="card shadow-sm h-100">
          <div class="card-header bg-primary text-white text-center fw-bold">
            <h4>📚 Danh Sách Bài Học</h4>
          </div>
          <ul class="list-group list-group-flush overflow-auto" style="max-height: 500px;">
            <li
              v-for="(bai, index) in list_bai_hoc"
              :key="bai.id ?? index"
              class="list-group-item list-hover cursor-pointer d-flex align-items-center"
              :class="{ 'active-item': bai.id === baiDangHoc?.id }"
              @click="chonBaiHoc(bai)"
            >
              <span class="me-2 badge bg-secondary">Bài {{ bai.bai_hoc_so }}</span>
              <span>{{ bai.tieu_de }}</span>
            </li>
            <li v-if="!list_bai_hoc.length" class="list-group-item text-center text-muted">
              Chưa có bài học nào
            </li>
          </ul>
        </div>
      </div>

      <div class="col-lg-8 col-md-12">
        <div class="card shadow-sm h-100">
          <div class="card-header bg-light fw-bold text-center">
            <h3>{{ baiDangHoc?.tieu_de || "Chưa chọn bài học" }}</h3>
          </div>
          <div class="card-body text-center">
            <iframe
              v-if="baiDangHoc?.link_bai_hoc"
              :src="getEmbedUrl(baiDangHoc.link_bai_hoc)"
              width="100%"
              height="450"
              class="rounded shadow-sm"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
            <p v-else class="text-muted mt-3">
              🎬 Vui lòng chọn một bài học để bắt đầu
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: {
    id: { type: [String, Number], default: null },
  },
  data() {
    return {
      list_bai_hoc: [],
      baiDangHoc: null,
      loading: false,
      error: null,
    };
  },
  mounted() {
    this.layDanhSachBaiHoc();
  },
  watch: {
    id() {
      this.layDanhSachBaiHoc();
    },
    "$route.params.id"() {
      if (!this.id) this.layDanhSachBaiHoc();
    },
  },
  methods: {
    getEffectiveId() {
      const raw = this.id ?? this.$route.params.id ?? null;
      return !raw || String(raw) === "undefined" ? null : raw;
    },
    layDanhSachBaiHoc() {
      const idKhoaHoc = this.getEffectiveId();
      if (!idKhoaHoc) {
        this.error = "Không có id khóa học trong route.";
        return;
      }
      this.loading = true;
      this.error = null;

      axios
        .get(`http://127.0.0.1:8000/api/home-page/khoa-hoc/${idKhoaHoc}/bai-hoc`, {
          headers: { Authorization: "Bearer " + localStorage.getItem("key_khach_hang") },
        })
        .then((res) => {
          this.list_bai_hoc = res.data?.data ?? res.data ?? [];
          this.baiDangHoc = this.list_bai_hoc[0] || null;
        })
        .catch((err) => {
          this.error = err.response?.data?.message ?? "Lỗi khi lấy bài học";
        })
        .finally(() => {
          this.loading = false;
        });
    },
    chonBaiHoc(bai) {
      this.baiDangHoc = bai;
    },
    getEmbedUrl(url) {
      if (!url) return "";
      try {
        if (url.includes("youtube.com/embed") || url.includes("player.vimeo.com")) return url;
        if (url.includes("youtube.com/watch")) {
          const id = new URL(url).searchParams.get("v");
          return id ? `https://www.youtube.com/embed/${id}` : url;
        }
        if (url.includes("youtu.be/")) {
          const id = url.split("youtu.be/")[1].split(/[?&]/)[0];
          return `https://www.youtube.com/embed/${id}`;
        }
        return url;
      } catch {
        return url;
      }
    },
  },
};
</script>

<style scoped>
.cursor-pointer {
  cursor: pointer;
}
.list-hover:hover {
  background-color: #f8f9fa;
}
.active-item {
  background-color: #0d6efd !important;
  color: #fff !important;
  font-weight: 600;
}
</style>
