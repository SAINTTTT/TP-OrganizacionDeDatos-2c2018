# TP-OrganizacionDeDatos-2c2018
Trabajos practicos de la materia Organizacion de datos (95.58) de la Facultad de Ingenieria de la Universidad de Buenos Aires

# TP1: Analisis exploratorio de datos.    

Realizaremos un análisis de datos sobre un conjunto de eventos de web analytics de usuarios que visitaron www.trocafone.com, su plataforma de ecommerce de Brasil. Trocafone es un side to side Marketplace para la compra y venta de dispositivos electrónicos que se encuentra actualmente operando en Brasil y Argentina. 

La empresa realiza distintas actividades que van desde la implementación de plataformas de trade-in (conocidos en la Argentina como Plan Canje), logística directa y reversa, reparación y recertificación de dispositivos (refurbishing) y venta de productos recertificados por múltiples canales (ecommerce, marketplace y tiendas físicas). 

Para conocer más de su modelo de negocio, pueden visitar el siguiente artículo: https://medium.com/trocafone/el-maravilloso-mundo-de-trocafone-5bdc5761856b

Para acotar el alcance del trabajo práctico analizaremos un subconjunto de eventos de web analytics que Trocafone tiene disponible para una cantidad representativa de usuarios que visitaron su plataforma de ecommerce. 

El link para obtener el set de datos para el TP1 es el siguiente: https://drive.google.com/file/d/1gUddcLLujjFfwZslypUv1LESTM6KiwJn/view?usp=sharing

En el link pueden encontrar el archivo events.csv el cual contiene las siguientes columnas:

timestamp: Fecha y hora cuando ocurrió el evento. (considerar BRT/ART).
event: Tipo de evento
person: Identificador de cliente que realizó el evento.
url: Url visitada por el usuario.
sku: Identificador de producto relacionado al evento.
model: Nombre descriptivo del producto incluyendo marca y modelo.
condition: Condición de venta del producto
storage: Cantidad de almacenamiento del producto.
color: Color del producto
skus: Identificadores de productos visualizados en el evento.
search_term: Términos de búsqueda utilizados en el evento.
staticpage: Identificador de página estática visitada
campaign_source: Origen de campaña, si el tráfico se originó de una campaña de marketing
search_engine: Motor de búsqueda desde donde se originó el evento, si aplica.
channel: Tipo de canal desde donde se originó el evento.
new_vs_returning: Indicador de si el evento fue generado por un usuario nuevo (New) o por un usuario que previamente había visitado el sitio (Returning) según el motor de analytics.
city: Ciudad desde donde se originó el evento
region: Región desde donde se originó el evento.
country: País desde donde se originó el evento.
device_type: Tipo de dispositivo desde donde se genero el evento.
screen_resolution: Resolución de pantalla que se está utilizando en el dispositivo desde donde se genero el evento.
operating_system_version: Version de sistema operativo desde donde se origino el evento.
browser_version: Versión del browser utilizado en el evento 

Por otro lado, los siguientes tipos de eventos se encuentran disponibles (en el campo event) sobre los cuales se brinda una breve descripción:

“viewed product”: El usuario visita una página de producto.
“brand listing”: El usuario visita un listado específico de una marca viendo un conjunto de productos.
“visited site”: El usuario ingresa al sitio a una determinada url.
“ad campaign hit”: El usuario ingresa al sitio mediante una campana de marketing online.
“generic listing”: El usuario visita la homepage.
“searched products”: El usuario realiza una búsqueda de productos en la interfaz de búsqueda del site.
“search engine hit”: El usuario ingresa al sitio mediante un motor de búsqueda web.
“checkout”: El usuario ingresa al checkout de compra de un producto.
“staticpage”: El usuario visita una página
“conversion”: El usuario realiza una conversión, comprando un producto.
“lead”: El usuario se registra para recibir una notificación de disponibilidad de stock, para un producto que no se encontraba disponible en ese momento.

Algo a tener en cuenta es que no todos los datos descritos en las columnas corresponde a todos los tipos de eventos. 

Por otro lado es importante tener en cuenta que el carácter temporal de los eventos para un usuario nos indican una progresión de los mismos en el tiempo, por lo cual es factible analizarlos de esa forma.

Por último, deberian tener en cuenta que dado que los usuarios están navegando catálogos de productos hacia un flujo de compra en una página de producto es posible derivar información entre eventos para poder enriquecer unos y otros.

El objetivo del primer TP es realizar un análisis exploratorio del set de datos del TP. Queremos ver qué cosas podemos descubrir sobre los datos que puedan resultar interesantes.

# TP2: Predicciones utilizando algoritmos de Machine Learning.

El segundo trabajo práctico es una competencia de Machine Learning en donde cada grupo debe intentar determinar, para cada usuario presentado, cuál es la probabilidad de que ese usuario realice una conversión en Trocafone en un periodo determinado.

La competencia se desarrollará en la plataforma de Kaggle. En el siguiente link se provee la siguiente información para la competencia: https://drive.google.com/file/d/1kQujhvOKAU4EzhaYDbgquf_XKFt9sHMy/view?usp=sharing

En este podrán encontrar los siguientes archivos:

events_up_to_01062018.csv
labels_training_set.csv

El archivo events_up_to_01062018.csv contiene en el mismo formato utilizado en el TP1 información de eventos realizado en la plataforma para un conjunto de usuarios hasta el 31/05/2018.

Por otro lado el archivo labels_training_set.csv indica para un subconjunto de los usuarios incluidos en el set de eventos events_up_to_01062018.csv si los mismos realizaron una conversión (columna label = 1) o no (columna label = 0) desde el 01/06/2018 hasta el 15/06/2018. 

conversiones_train_pub = pd.read_csv('Data/Trocafone/Pub/labels_training_set.csv')
conversiones_train_pub.head()



person
label
0
0566e9c1
0
1
6ec7ee77
0
2
abe7a2fb
0
3
34728364
0
4
87ed62de
0


La información de estos archivos debe ser utilizada para entrenar un modelo de Machine Learning, de tal forma de poder indicar la probabilidad de que conjunto seleccionado de usuarios realice una conversión desde el 01/06/2018 al 15/06/2018. 

Se pedirá indicar esa probabilidad de conversión para usuarios que no se encuentran en el archivo labels_training_set.csv, pero para los cuales se cuenta con información en events_up_to_01062018.csv

El listado de estas personas será provisto en el archivo trocafone_kaggle_test.csv

personas_a_predecir = pd.read_csv('Data/Trocafone/trocafone_kaggle_test.csv')
personas_a_predecir.head()


person


0
4886f805


1
0297fc1e


2
2d681dd8


3
cccea85e


4
4c8a8b93




