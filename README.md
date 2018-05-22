# ERP前端

## 库
jQuery v1.11.3

## 工具
gulp + babel、npm、browserify

## gulp搭建
1.安装nodeJs  
2.cmd执行 `npm install gulp -g`  
3.在package.json同目录路径下，命令行执行npm install  
4.有部分会存在node未配置环境变量的情况，自行手动配置即可  

## 框架
`easyui + angularJs + layer(弹窗UI)`:html代码，运营管理，服务管理，售后管理（包含TAT版本），售后工单管理，门店售后管理，API管理，防窜货管理，经销商管理，客服管理，经销商报修，文档中心，快递管理，财务管理，miniui公共iframe弹窗 ，进存管理，登录，售后服务，个人中心，初始化文件，报表管理，翻新管理，门店销售模块，发货订单管理（第一版），店铺管理，管易店铺管理，门店端，门店店铺信息，供应链，系统设置，仓库管理（第一版）  
`miniui`：订单管理

## 插件
文件目录：`static/lib/plugin/`
> 剪贴板：clipboard.min.js  
> 城市：jquery.cityselect.js  
> 分页器：jquery.pageList.js  
> 下拉模糊搜索：jquery.searchData.js  

## 注意事项
1.支持ES6写法，babel编译同时引入polyfill，使用模块的部分需要使用browserify进行打包;  
2.src/static/lib/js/public/下的代码切记不可用browserify进行打包，否则会默认局部作用域，全局函数不起作用；  
3.全局操作权限变量：permission_limit_data；  
4.`easyui + angularJs + layer`引用过多，已使用gulp合并打包在 `static/lib/dist/bundle.min.js`，具体包含文件参照：`gulpfile.js` 内的 `concatjs`任务,注意区分cdn文件

## 文档结构
> 整体目录结构如下所示，图片，库、框架不做打包，直接放入static内，页面引用的js和css在lib下创建同目录同名文件,对初始化文件目录有详细文件介绍

> 公共css文件：`src/static/lib/css/common/standard.css`
> 公共js文件：
>> 主框架为easyui + angularJs + layer：`src/static/lib/js/common/function.js`，包含angular指令,已打包至`static/lib/dist/bundle.min.js`，详见注意事项第四条
>> 主框架为miniui：`src/static/lib/js/common/common.js`

```
.
├── gulpfile.js                                     // gulp配置文件
├── package.json                                    // 所需要的模块
├── templates                                       // 打包后html文件，放在服务器即可正常访问
├── static                                 			// 打包后静态资源，放在服务器即可正常访问
├── src                                         	// 源码目录
│   ├── static
│   │  	└──lib
│   │  		├──css									// css
│   │  		├──js									// JS
│   │  		└──plugin								// 插件
│	│
│	└── templates                              	    // html代码
│     	├──activity_operation						// 运营管理
│     	├──after_sales_service						// 服务管理
│     	├──aftersaleInvoices						// 售后管理（包含TAT版本）
│     	├──aftersaleManagement						// 售后工单管理
│     	├──afterSales								// 门店售后管理
│     	├──api										// API管理
│     	├──bugsellManagement						// 防窜货管理
│     	├──customerRelations						// 经销商管理
│     	├──customerService							// 客服管理
│     	├──dealerRepair								// 经销商报修
│     	├──documents								// 文档中心
│     	├──expressManage							// 快递管理
│     	├──financeManage							// 财务管理
│     	├──iframeModel								// miniui公共iframe弹窗 
│     	├──inventoryManagement						// 进存管理
│     	├──main										// 登录
│     	├──maintenanceManage						// 售后服务
│     	├──order									// 订单管理
│     	├──personal									// 个人中心
│     	├──public									// 初始化文件
│		│	├──403.html								// 403错误
│		│	├──404.html								// 404错误
│		│	├──500.html								// 500错误
│		│	├──base.html							// 主框架为angular和easyui时的继承模板页面
│		│	├──developPage.html						// 未知错误
│		│	├──error.html							// 正在开发中
│		│	├──index.html							// 桌面首页
│		│	├──nui_base.html						// 主框架miniui时的继承模板页面
│		│	└──offline.html							// 服务器宕机错误
│     	├──reporting								// 报表管理
│     	├──returnfactoryManagement					// 翻新管理
│     	├──salegoods								// 门店销售模块
│     	├──salesManagement							// 发货订单管理（第一版）
│     	├──shop_Management							// 店铺管理
│     	├──shop_Management_Guanyi					// 管易店铺管理
│     	├──storeManage								// 门店端
│     	├──storesinfo								// 门店店铺信息
│     	├──supplyChain								// 供应链
│     	├──system									// 系统设置
│     	└──warehouseManagement						// 仓库管理（第一版）
├──
.

```
