# **DubboAPI-项目档案信息获取** {#gaoych}

### **Step配置dubbo.xml文件：**

在dubbo.xml文件中引入接口服务:ProjectAPIService

&lt;!--项目档案 --&gt;

&lt;dubbo:referenceid="projectAPIService"interface="com.yyjz.icop.share.api.service.ProjectAPIService"url="dubbo://123.56.19.206:20885"check="false"/&gt;

![](file:///C:\Users\gaoych\AppData\Local\Temp\ksohtml\wps86B2.tmp.jpg)

### **Step配置Maven依赖:**

在impl层的pom.xml文件中引入共享业务中心的依赖:icop-share-api

&lt;!-- 共享业务中心依赖 --&gt;

&lt;dependency&gt;

&lt;groupId&gt;com.yyjz&lt;/groupId&gt;

&lt;artifactId&gt;icop-share-api&lt;/artifactId&gt;

&lt;version&gt;0.0.1-SNAPSHOT&lt;/version&gt;

&lt;/dependency&gt;

![](file:///C:\Users\gaoych\AppData\Local\Temp\ksohtml\wps86B3.tmp.jpg)

### **Step代码中引入服务:**

@Autowired

**private** ProjectAPIServiceprojectAPIService;

![](file:///C:\Users\gaoych\AppData\Local\Temp\ksohtml\wps86C4.tmp.jpg)

### **Step代码的方法区中使用service调用API方法：**

/\*\*

\* 查询项目，根据组织id

\*

\***@param** orgId

\***@return**

\*/

@RequestMapping\(value ="getProjectByOrgId"\)

@ResponseBody

**public** JsonBackData getProjectByOrgId\(@RequestParam StringorgId\) {

JsonBackDataback =**new** JsonBackData\(\);

**try** {

**ProjectBO projectBO = projectAPIService.queryProjectByOrgId\(orgId\);**

back.setBackData\(projectBO\);

back.setSuccess\(**true**\);

back.setBackMsg\("查询项目信息成功"\);

}**catch** \(BusinessExceptione\) {

back.setSuccess\(**false**\);

back.setBackMsg\("查询项目信息失败:"+e.getMessage\(\)\);

}

**return**back;

}

![](file:///C:\Users\gaoych\AppData\Local\Temp\ksohtml\wps86D4.tmp.jpg)

  
@font-face{  
font-family:"Times New Roman";  
}  
  
@font-face{  
font-family:"宋体";  
}  
  
@font-face{  
font-family:"Calibri";  
}  
  
@font-face{  
font-family:"Consolas";  
}  
  
p.MsoNormal{  
mso-style-name:正文;  
mso-style-parent:"";  
margin:0pt;  
margin-bottom:.0001pt;  
mso-pagination:none;  
text-align:justify;  
text-justify:inter-ideograph;  
font-family:Calibri;  
mso-fareast-font-family:宋体;  
mso-bidi-font-family:'Times New Roman';  
font-size:10.5000pt;  
mso-font-kerning:1.0000pt;  
}  
  
h3{  
mso-style-name:"标题 3";  
mso-style-noshow:yes;  
mso-style-next:正文;  
margin-top:13.0000pt;  
margin-bottom:13.0000pt;  
mso-para-margin-top:0.0000gd;  
mso-para-margin-bottom:0.0000gd;  
page-break-after:avoid;  
mso-pagination:lines-together;  
text-align:justify;  
text-justify:inter-ideograph;  
mso-outline-level:3;  
line-height:172%;  
font-family:Calibri;  
mso-fareast-font-family:宋体;  
mso-bidi-font-family:'Times New Roman';  
font-weight:bold;  
font-size:16.0000pt;  
mso-font-kerning:1.0000pt;  
}  
  
span.msoIns{  
mso-style-type:export-only;  
mso-style-name:"";  
text-decoration:underline;  
text-underline:single;  
color:blue;  
}  
  
span.msoDel{  
mso-style-type:export-only;  
mso-style-name:"";  
text-decoration:line-through;  
color:red;  
}  
@page{mso-page-border-surround-header:no;  
	mso-page-border-surround-footer:no;}@page Section0{  
margin-top:72.0000pt;  
margin-bottom:72.0000pt;  
margin-left:90.0000pt;  
margin-right:90.0000pt;  
size:595.3000pt 841.9000pt;  
layout-grid:15.6000pt;  
}  
div.Section0{page:Section0;}

### **API**

//根据项目ID得到项目

**public** ProjectBOqueryProjectById\(StringprojectId\)**throws** BusinessException;

//根据批量项目ids返回多个项目

**public** Map&lt;String,ProjectBO&gt; queryProjectBatchByIds\(List&lt;String&gt;ids\)**throws** BusinessException;

//根据组织ID得到项目

**public** ProjectBO queryProjectByOrgId\(StringorgId\)**throws** BusinessException;

//根据所属公司id和项目状态 查询所有项目 返回这个人所属组织下的所有项目id

**public** ArrayList&lt;String&gt; queryProjectId\(StringorgId,Stringprjstate\)**throws** BusinessException;

alue

