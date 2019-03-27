<template>
	<div class="container">
		<div class="card">
		<span class="top">班级</span><span class="biaoqian">*</span><br/><br>
		<input type="text" placeholder="请输入班级" v-model="course.courseName" class="input-box" /><br/>
			<span class="top">课程</span><span class="biaoqian">*</span><br/><br>
		<input type="text" placeholder="请输入课程名称" v-model="course.courseClass" class="input-box" /><br/>
		<span class="top">类型</span><span class="biaoqian">*</span><br/>
		<div>
		<input name="save" type="checkbox" class="save"><span class="title">学校课表班课</span><span class="title se">(学校课表班课就是学校安排课程表里的正式班课）</span>
		</div>
		<br>
		<p class="title">选择班课封面</p>
		<div class="preview" @click="handleClick()">
			<img :src="course.cover" class="cover" v-if="!show" />
			<img src="../assets/icon_add.png" class="icon-plus" v-if="show" />
			<input type="file" @change="getFile($event)" style="display: none;" id="coverFile" />	
			
		</div>
		<hr>
		<button @click="addCourse(course)" class="btn">确定</button>
		<button @click="submit($event)" class="btn qx">取消</button>
	
		</div>
	</div>
</template>

<script>
export default {
	name: 'NewCourse',
	data() {
		return {
				loginUserId: 1,
				course: {
					courseName: '',
					courseClass: '',
					cover: '',
				},
				file: '',
				show: true
			};
		},

	methods: {
		//点击图片预览区，即模拟点击文件选择组件
		handleClick: function() {
			document.getElementById('coverFile').click();
		},
		//图片预览
		getFile: function() {
			this.file = event.target.files[0];
			var windowURL = window.URL || window.webkitURL;
			this.course.cover = windowURL.createObjectURL(this.file);
			this.show = false;
		},
		addCourse: function(course) {
				var _this = this;
				this.$http({
					method: 'post',
					url: 'http://localhost:8080/api/course',
					data: {
						userId: _this.loginUserId,
						courseName: course.courseName,
						courseClass: course.courseClass,
						cover: course.cover,
						finished: 0
					}
				}).then(function() {
					alert('新增班课成功');
					_this.$router.push('/');
				});
				}
					}
				};
</script>
<style scoped>
.container {
	display: flex;
	flex-direction: column;
	padding-top: 20px;
	padding-left: 100px;
	background-color: #fff;
	margin-top: 20px;
	
}
.card{
	margin: 0 auto;
}
.input-box {
	width: 500px;
	height: 25px;
	margin-bottom: 40px;
	font-size: 14px;
}
.btn {
	margin-top: 20px;
	width: 100px;
	height: 30px;
	border: 1px solid rgb(0, 187, 221);
	background-color: #fff;
	
	outline: none;
	color: rgb(0, 187, 221);
	font-size: 16px;
	margin-left: 80px;
}
.qx{
	margin-left: 100px;
	border: 1px solid rgb(148, 148,148);
	color: rgb(148, 148,148);
}
.preview {
	width: 100px;
	height: 100px;
	border: 2px dashed #aaa;
	cursor: pointer;
	display: flex;
	align-items: center;
	justify-content: center;
}
.icon-plus {
	width: 60px;
	height: 60px;
}
.cover {
	width: 100%;
	height: 100%;
}
.save {
	float: left;
}
.title{
	font-size: 13px;
	
}
.se{
	color:#6695CF;
} 
.biaoqian{
	color: #FF0000;
}
.top{
	font-size: 13px;
}
</style>
