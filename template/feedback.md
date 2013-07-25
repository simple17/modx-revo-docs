# Форма обратной связи

Установить пакет FormIt

## Чанки

### FeedBack

	<div class="form-contacts">
		<h3>Форма обратной связи</h3>
		[[!FormIt?
		&hooks=`spam,email` 
		&emailTpl=`tpl.FormIt.letter._FeedBack` 
		&emailTo=`[[#ID-РЕСУРСА-С-НАСТРОЙКАМИ.tv.settings_email]]`
		&emailFrom=`КАКОЙ-ТО-ЯЩИК@yandex.ru` 
		&emailSubject=`Обратная связь`
		&successMessage=`Благодарим Вас за проявленный интерес. В кратчайшие сроки наш специалист свяжется с Вами.`
		&validate=`
		name:required,
		contacts:required,
		comment:required
		`
		]] 
		<form action="[[~[[*id]]]]#form" method="post" class="form">
			<a name="form"></a>
			<input type="hidden" name="nospam:blank" value="" />
			<input type="hidden" name="pageid" value="[[*id]]" />
			<input type="hidden" name="pagetitle" value="[[*pagetitle:esc:htmlent]]" />

			[[!+fi.successMessage:notempty=`<p><strong>[[!+fi.successMessage]]</strong></p>`]]
			[[!+fi.error_message:notempty=`<p class="error">[[!+fi.error_message]]</p>`]]


			<label class="[[!+fi.error.name:notempty=` error `]]" for="name">
			Фамилия Имя<em>*</em>
			</label>
			<input type="text" name="name" id="name" value="[[!+fi.name]]" required class="[[!+fi.error.name:notempty=` error `]]" /> 
			[[!+fi.error.name:notempty=`[[!+fi.error.name]]<br/><br/>`]]

			<label class="[[!+fi.error.contacts:notempty=` error `]]" for="contacts">
			E-mail, телефон для связи<em>*</em>
			</label>
			<textarea type="text" name="contacts" id="contacts" value="[[!+fi.contacts]]" cols="55" rows="3" required class="[[!+fi.error.contacts:notempty=` error `]]" >[[!+fi.contacts]]</textarea> 
			[[!+fi.error.contacts:notempty=`[[!+fi.error.contacts]]<br/><br/>`]]

			<label class="[[!+fi.error.comment:notempty=` error `]]" for="comment">
			Меня интересует<em>*</em>
			</label>
			<textarea type="text" name="comment" id="comment" value="[[!+fi.comment]]" cols="55" rows="7" required class="[[!+fi.error.comment:notempty=` error `]]" >[[!+fi.comment]]</textarea> 
			[[!+fi.error.comment:notempty=`[[!+fi.error.comment]]<br/><br/>`]]

			<div class="form-buttons">
				<input type="submit" value="Отправить" class="secondary button right" />
			</div>
		</form>
	</div>


### tpl.FormIt.letter._FeedBack

	<p><b>[[+name]]</b> отправил сообщение.</p>
	<dl>
		<dt>Контакты:</dt>
		<dd>[[+contacts]]</dd>

		<dt>Интересует:</dt>
		<dd>[[+comment]]</dd>
	</dl>

## Настройки SMTP
