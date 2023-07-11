![WPS图片(5)](https://github.com/zry-wyj/cve/assets/139187135/a763966b-3bb9-4ac3-b0fc-94672cca41b8)SQL injection vulnerability exists in ibos oa v4.5.5

official website:http://www.ibos.com.cn/

version:4.5.5

Function point: Export this page from the personal office address book

![WPS图片(1)](https://github.com/zry-wyj/cve/assets/139187135/bebdf616-4800-48a7-9bbc-c18622b90755)

POC

Route: r=contact/default/export

Parameter: uids

Successfully delayed injection through stack injection

![WPS图片(2)](https://github.com/zry-wyj/cve/assets/139187135/f8b2db67-1bab-45e5-9716-0835997b0e4b)

analyze

Here, the actionExport() method is called first, and then the functionality is executed by calling the export() method under the base class BaseController

![WPS图片(3)](https://github.com/zry-wyj/cve/assets/139187135/aee7a5cf-b950-429d-a4b4-f593dc830c31)


The getUserData() method is called in export(), where the SQL query is performed by getting the uids parameter
![WPS图片(4)](https://github.com/zry-wyj/cve/assets/139187135/911f1d30-d497-456b-aaf0-cb4fa609821c)

Here, the fetchAllByUids() under model is called for SQL encapsulation execution



![WPS图片(5)](https://github.com/zry-wyj/cve/assets/139187135/dbdd83e0-73c0-4baf-b228-5f2be5f5260b)

![WPS图片(6)](https://github.com/zry-wyj/cve/assets/139187135/934bac0c-2bdb-4433-b7ed-1297cbcdc541)
![WPS图片(7)](https://github.com/zry-wyj/cve/assets/139187135/7c855d64-3b5b-4a04-ba85-edf4d08d343b)
