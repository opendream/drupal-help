ปัญหา Browser พยายามอยากจะ render pdf file...

แก้ได้ 2 ทางคือ 

1. ลง force_file แต่มันจะสร้าง path ขึ้นมาโดยใช้ hook_menu แล้วก็ไปแก้ไข header ข้อเสียก็.. path มันจะเปลี่ยน เป็น system/file_force/blahblah?dl=1
2. แก้โดย เอา .htaccess เข้าไปวางไว้ใน sites/default/files/.htaccess โดยมีเนื้อหาแบบนี้

		<IfModule mod_headers.c>
		<FilesMatch "\.(pdf|PDF)">
			ForceType application/octet-stream
			Header set Content-Disposition attachment
		</FilesMatch>
		</IfModule>

ถ้าไม่เห็นผลให้

1. chrome/safari จะ cache เก่ง ให้เทสด้วย incognito mode ง่ายสุดให้เทสด้วย Firefox
2. ถ้ายังไม่ให้อีกให้เช็ค mod_headers.c เปิดด้วยคำสั่ง `a2enmod headers` แล้ว restart apache
