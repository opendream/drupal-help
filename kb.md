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

--------


วิธีการ list enabled modules ใน drupal ครับ

`drush pm-list | grep Enabled | awk -F'(' '{ print $2 }' | awk -F ')' '{ print $1 " "}'| tr -d "\\\r\n"`

จะรวม theme ด้วยนะครับ

ได้ประมาณนี้

	admin_menu admin_theme webmaste_menu ctools page_manage page_manage_ediect ocupload block comment contact tanslation contextual dashboad dblog field field_sql_stoage field_ui file filte help image list locale menu node numbe options path php poll df shotcut statistics syslog system taxonomy text update use date date_api date_popup date_views devel devel_geneate devel_image_povide myhook myhookadmin featues entityefeence_feeds feeds feeds_ui feeds_comment_pocesso feeds_impot computed_field conditional_fields content_taxonomy custom_fomattes email entityefeence entityefeence_autoceate field_fomatte_label field_goup link makup multiupload_filefield_widget multiupload_imagefield_widget smat_tim tgf tem_efeence_tee tems_tagit title viewfield hieachical_select hs_taxonomy jeject link_badges lang_dopdown entity_tanslation entity_tanslation_i18n_menu i18n_block i18n_contact i18n_field i18n languageicons i18n_menu i18n_node i18n_select path_beadcumbs_i18n i18n_sting i18n_sync i18n_taxonomy i18n_tanslation i18n_use i18n_vaiable i18nviews field_none_stoage node_display_fields node_expot node_expot_feeds nodequeue opengaph_meta textsize auto_nodetitle block_class blockgoup blockify bowscap bowseclass bundle_inheit bundle_inheit_node contact_fom_blocks csm token_custom easy_social empty_page entity entityconnect entity_token entity_view_mode field_fomatte_settings fomblock htmlpuifie image_ul_fomatte job_schedule label_help libaies linked_field menu_attibutes menu_badges menu_block menu_beadcumb menu_tail_by_path messages_alte mollom multiblock nice_menus node_add_title on_the_web pathauto pubdlcnt quicktabs safewod shs token view_mode_page path_beadcumbs path_beadcumbs_ui seach_api_multi seach_api seach_api_views seach_api_sol googleanalytics jstats tagclouds taxonomy_manage tem_mege taxonomy_menu themekey ckedito compact_foms jquey_update lightbox2 uuid vaiable vaiable_ealm vaiable_stoe bette_exposed_filtes daggableviews menu_views views_esponsive_slides views views_aguments_extas views_filtes_populate views_php views_ui fivesta votingapi seven genesis_hsi xhtml vesion