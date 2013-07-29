# Настройка галереи

*Установить компонент Gallery*

## Чанк tpl.Gallery.thumb._gallery
	<div class="span2 item">
		<a href="[[+linkToImage:if=`[[+linkToImage]]`:is=`1`:then=`[[+image_absolute]]`:else=`[[~[[*id]]?
				&[[+imageGetParam]]=`[[+id]]`
				&[[+albumRequestVar]]=`[[+album]]`
				&[[+tagRequestVar]]=`[[+tag]]` ]]`]]" title="[[+name]]" [[+link_attributes]]>
			<img class="[[+imgCls]]" src="[[+thumbnail]]" alt="[[+name]]" [[+image_attributes]] />
		</a>
	</div>
	
## Чанк Галерея
	[[includeJsCss? &js=`template/js/jquery.fancybox.pack.js` &css=`template/css/jquery.fancybox.css`]]
	<div class="row gallery">
		[[Gallery? &album=`[[+name]]` &thumbTpl=`tpl.Gallery.thumb._gallery` &thumbWidth=`140` &thumbHeight=`90` &imageFar=`0` &imageZoomCrop=`1` &limit=`[[+limit]]`]]
	</div>