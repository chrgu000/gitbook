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



### **API**

//根据项目ID得到项目

**public** ProjectBOqueryProjectById\(StringprojectId\)**throws** BusinessException;

//根据批量项目ids返回多个项目

**public** Map&lt;String,ProjectBO&gt; queryProjectBatchByIds\(List&lt;String&gt;ids\)**throws** BusinessException;

//根据组织ID得到项目

**public** ProjectBO queryProjectByOrgId\(StringorgId\)**throws** BusinessException;

//根据所属公司id和项目状态 查询所有项目 返回这个人所属组织下的所有项目id

**public** ArrayList&lt;String&gt; queryProjectId\(StringorgId,Stringprjstate\)**throws** BusinessException;



