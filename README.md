# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# Soporte para varios idiomas
_
Internacionalización
El sistema de internacionalización o I18N nos ayuda a interactuar con una libreria de Rails para insertar de forma automatizada ciertas keys para enlazar traducciones a diferentes idiomas.

_

Cómo usarlo

En los labels de los atributos del modelo User escribiremor t(‘model.atribute’). Esto, de forma automática accederá al atributo del modelo.
Buscamos el archivo config/locales/en.yml Este archivo contendrá “etiquetas”. Colocamos el nombre del modelo y sus atributos. Dentro de estas etiquetas colocaremos su traducción.
en:
  hello: Hello world
  users:
    first_name: First name
El archivo “en” funciona como diccionario del idioma ingles. Para crear uno del idioma español podemos duplicarlo y llamarlo “en”. En el archivo en colocaremos los términos en español.
Para ahorrarnos el proceso de escribir cada atributo de forma manual podemos usar el comando i18n-asks add-missing. Esto requiere una unstalacion (gem install i18n-tasks).
_

Establecer lenguaje por acciones

Vamos al controlador que queremos internacionalizar podemos añadir la clase I18n y el método locale, para establecer el lenguaje de la acción. ‘es’.
def new
	I18n.locale = 'es'
	@user = User.new
end
_
Establecer lenguaje por controlador

Si queremos que esta internacionalización afecte a todas las acciones tendríamos que ir a su controlador base. Dentro de este colocaremos dentro de la clase:
before_Action :set_locale

def set_locale
	I18n.locale = 'es'
end
