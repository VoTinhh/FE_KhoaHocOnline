<template>
    <div class="row">
        <div class="col-lg-12">
            <div class="card">
                <div class="card-body">
                    <ul class="nav nav-tabs nav-primary" role="tablist">
                        <li class="nav-item" role="presentation">
                            <a class="nav-link active" data-bs-toggle="tab" href="#primaryhome" role="tab"
                                aria-selected="true">
                                <div class="d-flex align-items-center">
                                    <div class="tab-icon"><i class="fa-solid fa-user font-18 me-1"></i>
                                    </div>
                                    <div class="tab-title">Profile</div>
                                </div>
                            </a>
                        </li>
                        <li class="nav-item" role="presentation">
                            <a class="nav-link" data-bs-toggle="tab" href="#primarycontact" role="tab"
                                aria-selected="false" tabindex="-1">
                                <div class="d-flex align-items-center">
                                    <div class="tab-icon"><i class="fa-solid fa-lock font-18 me-1"></i>
                                    </div>
                                    <div class="tab-title">Đổi mật khẩu</div>
                                </div>
                            </a>
                        </li>
                        <li class="nav-item" role="presentation">
                            <a class="nav-link" data-bs-toggle="tab" href="#naptienTK" role="tab" aria-selected="false"
                                tabindex="-1">
                                <div class="d-flex align-items-center">
                                    <div class="tab-icon me-1"><i class="fa-solid fa-money-check-dollar"></i>
                                    </div>
                                    <div class="tab-title">Nạp Tiền</div>
                                </div>
                            </a>
                        </li>
                    </ul>
                    <div class="tab-content py-3">
                        <div class="tab-pane fade show active" id="primaryhome" role="tabpanel">
                            <div class="row">
                                <div class="col-lg-4 d-flex">
                                    <div class="card flex-fill">
                                        <div class="card-body">
                                            <div class="d-flex flex-column align-items-center text-center">
                                                <img src="https://media.istockphoto.com/id/1171965518/vi/vec-to/bi%E1%BB%83u-t%C6%B0%E1%BB%A3ng-ng%C6%B0%E1%BB%9Di-kinh-doanh-b%E1%BB%8B-c%C3%B4-l%E1%BA%ADp-tr%C3%AAn-n%E1%BB%81n-tr%E1%BA%AFng-t%E1%BB%95-ch%E1%BB%A9c-k%C3%BD-k%E1%BA%BFt-kinh-doanh-l%C3%A0m-vi%E1%BB%87c-theo.jpg?s=612x612&w=0&k=20&c=sO7FRTTJT3dqiyPL5orDp057r_nsbu9yMNrGAP-SlMk="
                                                    style="width: 140px; height: 140px;"
                                                    class="rounded-circle p-1 bg-primary">
                                                <div class="mt-3">
                                                    <h4>{{ thong_tin.ho_va_ten }}</h4>
                                                    <p class="text-secondary mb-1">{{ thong_tin.email }}</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                                <div class="col-lg-8 d-flex">
                                    <div class="card flex-fill">
                                        <div class="card-body">
                                            <div class="row mb-3">
                                                <div class="col-lg-3">
                                                    <h6 class="mb-0">Họ và Tên</h6>
                                                </div>
                                                <div class="col-lg-9 text-secondary">
                                                    <input type="text" v-model="thong_tin.ho_va_ten"
                                                        class="form-control" placeholder="Nhập họ và tên">
                                                </div>
                                            </div>
                                            <div class="row mb-3">
                                                <div class="col-lg-3">
                                                    <h6 class="mb-0">Email</h6>
                                                </div>
                                                <div class="col-lg-9 text-secondary">
                                                    <input disabled v-model="thong_tin.email" type="text"
                                                        class="form-control" placeholder="Nhập email">
                                                </div>
                                            </div>
                                            <div class="row mb-3">
                                                <div class="col-lg-3">
                                                    <h6 class="mb-0">Số Điện Thoại</h6>
                                                </div>
                                                <div class="col-lg-9 text-secondary">
                                                    <input v-model="thong_tin.so_dien_thoai" type="text"
                                                        class="form-control" placeholder="Nhập số điện thoại">
                                                </div>
                                            </div>
                                            <div class="row mb-3">
                                                <div class="col-lg-3">
                                                    <h6 class="mb-0">Ngày Sinh</h6>
                                                </div>
                                                <div class="col-lg-9 text-secondary">
                                                    <input v-model="thong_tin.ngay_sinh" type="date"
                                                        class="form-control" placeholder="Nhập ngày sinh">
                                                </div>
                                            </div>
                                            <div class="row">
                                                <div class="col-lg-3"></div>
                                                <div class="col-lg-9 text-secondary">
                                                    <button type="button" class="btn btn-primary px-4"
                                                        @click="thayDoiThongTin()">Lưu</button>
                                                </div>
                                            </div>
                                        </div>
                                    </div>

                                </div>
                            </div>
                        </div>
                        <div class="tab-pane fade" id="primarycontact" role="tabpanel">
                            <div class="col text-center mb-4">
                                <h4 class="fw-bold">Thay đổi mật khẩu</h4>
                                <p class="text-muted">Quản lý mật khẩu để bảo mật tài khoản của bạn</p>
                            </div>

                            <div class="row justify-content-center">
                                <div class="col-lg-5 col-md-8">
                                    <div class="card shadow-lg border-0 rounded-3">
                                        <div class="card-body p-4">

                                            <div class="mb-3">
                                                <label class="form-label fw-semibold">Mật khẩu cũ</label>
                                                <div class="input-group">
                                                    <span class="input-group-text"><i
                                                            class="fa-solid fa-lock"></i></span>
                                                    <input v-model="doi_mat_khau.old_password" type="password"
                                                        class="form-control" placeholder="Nhập mật khẩu cũ">
                                                </div>
                                            </div>

                                            <div class="mb-3">
                                                <label class="form-label fw-semibold">Mật khẩu mới</label>
                                                <div class="input-group">
                                                    <span class="input-group-text"><i
                                                            class="fa-solid fa-key"></i></span>
                                                    <input v-model="doi_mat_khau.new_password" type="password"
                                                        class="form-control" placeholder="Nhập mật khẩu mới">
                                                </div>
                                            </div>

                                            <div class="mb-4">
                                                <label class="form-label fw-semibold">Nhập lại mật khẩu mới</label>
                                                <div class="input-group">
                                                    <span class="input-group-text"><i
                                                            class="fa-solid fa-key"></i></span>
                                                    <input v-model="doi_mat_khau.re_password" type="password"
                                                        class="form-control" placeholder="Xác nhận mật khẩu mới">
                                                </div>
                                            </div>

                                            <div class="d-grid">
                                                <button class="btn btn-primary btn-lg rounded-pill"
                                                    @click="doiMatKhau()">
                                                    <i class="fa-solid fa-save me-2"></i>Lưu thay đổi
                                                </button>
                                            </div>

                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="tab-pane fade" id="naptienTK" role="tabpanel">
                            <div class="col text-center mb-4">
                                <h4 class="fw-bold">Nạp Tiền Tài Khoản</h4>
                                <p class="text-muted">Vui lòng nhập số tiền bạn muốn nạp vào tài khoản</p>
                            </div>

                            <div class="row justify-content-center">
                                <div class="col-lg-5 col-md-8">
                                    <div class="card shadow-lg border-0 rounded-3">
                                        <div class="card-body p-4">
                                            <div class="mb-3">
                                                <label class="form-label fw-semibold">Nhập số tiền nạp</label>
                                                <div class="input-group">
                                                    <span class="input-group-text"><i
                                                            class="fa-solid fa-coins"></i></span>
                                                    <input v-model="so_tien_nap" type="number" min="1000" step="1000"
                                                        class="form-control" placeholder="Ví dụ: 50000">
                                                </div>
                                                <small class="text-muted">Số tiền tối thiểu: 100,000 VNĐ</small>
                                            </div>

                                            <div class="d-grid">
                                                <button v-on:click="xacNhanNapTien()"
                                                    class="btn btn-primary btn-lg rounded-pill" data-bs-toggle="modal"
                                                    data-bs-target="#xacNhanNapTienModal">
                                                    <i class="fa-solid fa-wallet me-2"></i>Nạp Tiền
                                                </button>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal nạp tiền -->
    <div class="modal fade" id="xacNhanNapTienModal" tabindex="-1" aria-labelledby="exampleModalLabel"
        aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h1 class="modal-title fs-5" id="exampleModalLabel">Xác Nhận Nạp Tiền</h1>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-12">
                            <div class="card">
                                <div class="card-body">
                                    <div class="alert alert-success" role="alert">
                                        Bạn phải quét mã QR để thanh toán nạp tiền vào tài khoản
                                    </div>
                                    <img :src="link_qr" class="img-fluid">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios';

export default {
    data() {
        return {
            so_tien_nap: 0,
            link_qr: '',
            thong_tin: {},
            doi_mat_khau: {}
        }
    },
    mounted() {
        this.layThongTinKhachHang();
    },
    methods: {
        doiMatKhau() {
            axios
                .post("http://127.0.0.1:8000/api/khach-hang/doi-mat-khau-profile", this.doi_mat_khau, {
                    headers: {
                        Authorization: 'Bearer ' + localStorage.getItem("key_khach_hang")
                    }
                })
                .then((res) => {
                    if (res.data.status) {
                        this.$toast.success(res.data.message);
                        this.layThongTinKhachHang();

                    } else {
                        this.$toast.error(res.data.message);
                        // this.$router.push('/');
                    }
                })
                .catch((res) => {
                    const list = Object.values(res.response.data.errors);
                    list.forEach((v, i) => {
                        this.$toast.error(v[0]);
                    });
                })
        },
        layThongTinKhachHang() {
            axios
                .get("http://127.0.0.1:8000/api/khach-hang/lay-thong-tin-profile", {
                    headers: {
                        Authorization: 'Bearer ' + localStorage.getItem("key_khach_hang")
                    }
                })
                .then((res) => {
                    if (res.data.status) {
                        this.thong_tin = res.data.thong_tin;
                    } else {
                        this.$toast.error(res.data.message);
                        this.$router.push('/');
                    }
                })
        },
        thayDoiThongTin() {
            axios
                .post("http://127.0.0.1:8000/api/khach-hang/thay-doi-thong-tin-profile", this.thong_tin, {
                    headers: {
                        Authorization: 'Bearer ' + localStorage.getItem("key_khach_hang")
                    }
                })
                .then((res) => {
                    if (res.data.status) {
                        this.$toast.success(res.data.message);
                        this.layThongTinKhachHang();

                    } else {
                        this.$toast.error(res.data.message);
                        this.$router.push('/');
                    }
                })
                .catch((res) => {
                    const list = Object.values(res.response.data.errors);
                    list.forEach((v, i) => {
                        this.$toast.error(v[0]);
                    });
                })
        },
        xacNhanNapTien() {
            var payload = {
                'so_tien_nap': this.so_tien_nap
            }
            axios
                .post("http://127.0.0.1:8000/api/khach-hang/xac-nhan-nap-tien", payload, {
                    headers: {
                        Authorization: 'Bearer ' + localStorage.getItem("key_khach_hang")
                    }
                })
                .then((res) => {
                    if (res.data.status) {
                        this.$toast.success(res.data.message)
                        var noi_dung_chuyen_tien = res.data.noi_dung_chuyen_tien;
                        this.link_qr = "https://img.vietqr.io/image/970422-0848012945-compact2.png?amount=" + this.so_tien_nap + "&addInfo=" + noi_dung_chuyen_tien + "&accountName=HOCMAI"
                    }
                })
        }
    },
}
</script>
<style></style>