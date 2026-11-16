..::CURSO DJANGO 2026::..
	..::CESM::..
	----URLS--

#################################################
1. Crea una App llamada empleados:
    python manage.py startapp empleados
#################################################
2.Registrar la app en el proyecto principal
• Abre el archivo poyecto1/settings.py.
• Busca la lista llamada INSTALLED_APPS.
• Agrega el nombre de tu aplicación al final de la lista:
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'empleados',  # <-- Agrega esta línea
]

###############################################
3. Crear una vista de prueba en la app
• Abre el archivo empleados/views.py.
• Crea una función sencilla para comprobar que 
las rutas funcionan correctamente:

from django.http import HttpResponse

def inicio_empleados(request):
    return HttpResponse("Hola a todos desde empleados")
################################################
4. Crear el archivo urls.py dentro de la app
• Django no crea este archivo automáticamente dentro de 
  las aplicaciones. Crea un archivo nuevo llamado urls.py 
  dentro de la carpeta empleado/ (al mismo nivel que views.py y
  models.py).
• Escribe la estructura básica de rutas apuntando a tu vista:
  from django.urls import path
  from . import views

	urlpatterns = [
   	 path('', views.inicio_empleados, name='inicio_empleado'),
	]
################################################
5. Conectar las rutas de la app al proyecto principal
• Abre el archivo poyecto1/urls.py.
• Importa la función include desde django.urls y
  enlaza el archivo que creaste en el paso anterior:

   from django.contrib import admin
   from django.urls import path, include  # <-- Importa include

   urlpatterns = [
    path('admin/', admin.site.urls),
    path('empleado/', include('empleados.urls')),  # <-- Enlaza las rutas de tu app
   ]

