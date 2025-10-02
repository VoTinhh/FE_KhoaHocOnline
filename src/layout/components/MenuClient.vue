<template>
	<div class="nav-container primary-menu">
		<div class="mobile-topbar-header">
			<div>
				<img src="https://i.pinimg.com/474x/7f/f4/a9/7ff4a90e1d5c45f7c0e1bf7ef772ba27.jpg" class="logo-icon" alt="logo icon">
			</div>
			<div>
				<h4 class="logo-text">HOCMAI</h4>
			</div>
			<div class="toggle-icon ms-auto"><i class='bx bx-arrow-to-left'></i>
			</div>
		</div>
		<nav class="navbar navbar-expand-xl w-100">
			<ul class="navbar-nav justify-content-start flex-grow-1 gap-1">
				<li class="nav-item">
					<router-link to="/">
						<a class="nav-link" href="/">
							<div class="parent-icon"><i class='bx bx-home-circle'></i>
							</div>
							<div class="menu-title">Home</div>
						</a>
					</router-link>
				</li>
				<li class="nav-item">
					<router-link to="/bai-viet">
						<a class="nav-link" href="/bai-viet">
							<div class="parent-icon"><i class="fa-solid fa-newspaper"></i>
							</div>
							<div class="menu-title">Bài Viết</div>
						</a>
					</router-link>
				</li>
				<li class="nav-item">
					<router-link to="/trac-nghiem">
						<a class="nav-link" href="/trac-nghiem">
							<div class="parent-icon"><i class="fa-solid fa-list-check"></i>
							</div>
							<div class="menu-title">Trắc Nghiệm</div>
						</a>
					</router-link>
				</li>
				<li class="nav-item">
					<router-link to="/danh-sach-khoa-hoc">
						<a class="nav-link" href="/danh-sach-khoa-hoc">
							<div class="parent-icon"><i class="fa-solid fa-warehouse"></i>
							</div>
							<div class="menu-title">Khóa Học Đăng Ký</div>
						</a>
					</router-link>
				</li>
				<li class="nav-item">
					<router-link to="/profile">
						<a class="nav-link" href="/profile">
							<div class="parent-icon"><i class="fa-solid fa-user"></i>
							</div>
							<div class="menu-title">Profile</div>
						</a>
					</router-link>
				</li>
			</ul>
		</nav>
	</div>
</template>
<script>
export default {

}
</script>
<style></style>