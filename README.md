# Note
入坑记录
  
  1.访问上传图片接口时，为何要在接口前加`/api`才能正常访问?  
  不太懂，项目是用renren-fast-vue框架，/api是设置的代理地址拦截，猜测可能因为提交的是formdata格式吧 = =  

***
  2.同一个项目，引用static里的文件在本地正常，打包到服务器访问不到  
  改成相对路径没用（可能是因为项目不再服务器根目录？），看网上说“资源用绝对路径引入时，读取的是public文件夹里的资源。如果应用没有部署在域名的根部，那么需要为 URL 配置 publicPath前缀”，根据框架配置，地址前加上window.SITE_CONFIG.cdnUrl得到解决（该值是打包后域名+版本号）  

***
  3.tinymce的坑，再次进入富文本页面，富文本内容不能操作  
  有说是需要tinymce.remove()销毁tinymce，尝试过后再次进来页面富文本有时加载不了，init出错。后来在editor加上key值，每次让key值自加，这样不需要销毁，每次也都能正常初始化。  
`<editor v-model="dataForm.content" id="tinymceId" :key="tinymceFlag" :init="editorInit"></editor>`
