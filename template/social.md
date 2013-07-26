# Социальные сети

## Кнопки социальных сетей

### Дополнительные параметры

Создать дополнительные параметы для шаблона "Пользовательские настройки".

* settings_social_fb
* settings_social_vk
* settings_social_tw

*Список можно дополнить*

### Чанк Social
*Переделать на fastField*

	<div class="soctext">Мы в соц. сетях:</div>
	[[$Set:isnot=``:then=`<a href="[[$Set? &name=`settings_social_vk`]]" target="_Blank"><img src="/assets/template/img/vk.png" alt="SEBC Vk"></a>`? &name=`settings_social_vk`]]
	[[$Set:isnot=``:then=`<a href="[[$Set? &name=`settings_social_fb`]]" target="_Blank"><img src="/assets/template/img/fb.png" alt="SEBC Facebook"></a>`? &name=`settings_social_fb`]]
	[[$Set:isnot=``:then=`<a href="[[$Set? &name=`settings_social_tw`]]" target="_Blank"><img src="/assets/template/img/tw.png" alt="SEBC Twitter"></a>`? &name=`settings_social_tw`]]
	
### Несколько кнопок для лайков и поделиться
	
*Взять из фг*