# Crear un Bucket 
## Introducción

rendimiento a escala en nube que ofrece durabilidad de datos confiable y rentable. El servicio Object Storage puede almacenar una cantidad ilimitada de datos no estructurados de cualquier tipo de contenido, incluidos datos analíticos y contenido enriquecido como imágenes y videos.

En este laboratorio aprenderá cómo trabajar con Object Storage dentro de Oracle Cloud Infrastructure.


*Tiempo estimado para este laboratorio: 10 minutos*.

### Objetivos

- Crear un Bucket en OCI.
- Crear un site estático utilizando un Bucket.

### Pasos
- [Tarea 1: Crear un Bucket](#tarea-1-crear-un-bucket)
- [Tarea 2: Configuración de Bucket](#tarea-2-configuración-de-bucket)
- [Tarea 3: Formatear el Block Volume y montar en la instancia](#tarea-3-formatear-el-block-volume-y-montar-en-la-instancia)

### Tarea 1: Crear un Bucket.

1. En el menú principal, de clic en la sección de **Storage** y posteriormente dirígete a **Buckets** 

![imagen](../Lab5-ObjectStorage/Imagenes/Imagen14.png)

2.	Luego haga clic en **Create Bucket**.

![imagen](../Lab5-ObjectStorage/Imagenes/Imagen15.png)

3. Complete el formulario como se muestra a continuación y haga clic en **Create**
a.	**Bucket Name:** "Ingrese un nombre para su Bucket".
b.	**Default Storage Tier:** Standard. 
c.	**Enable Object Versioning:** Activado.

![imagen](../Lab5-ObjectStorage/Imagenes/Imagen16.png)

### Tarea 2: Configuración de Bucket.
1.	En su Bucket, haga clic en el ícono de tres puntos y luego seleccione la opción **Edit**.

![imagen](../Lab5-ObjectStorage/Imagenes/Imagen17.png)

2.	Cambie la visibilidad a "Public", desmarque la opción "Allow users to list objects from this bucket" y haga clic en **Save Changes.**

![imagen](../Lab5-ObjectStorage/Imagenes/Imagen18.png)

### Tarea 3: Formatear el Block Volume y montar en la instancia

1. Ingrese a su Bucket.
2. Haga clic en **Objects**, en el menú del izquierdo, y de cluc en **Upload**
 
 ![imagen](../Lab5-ObjectStorage/Imagenes/Imagen19.png) 

3.	Copie el html a continuación y cree el archivo index.html usando un editor de texto (bloc de notas) Nota: Recuerda guardar el archivo con la extensión ".html" 
    ```sh
        <!DOCTYPE html>
        <html lang="pt-br">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>LAB: OCI FAST TRACK</title>
        </head>
        <body>
            <center> <img src="https://objectstorage.us-ashburn-1.oraclecloud.com/n/id3kyspkytmr/b/workshops-materiais/o/ocifasttracklogo.jpg"
         alt="LOGO OCI FAST TRACK">
                    <h1>Site estático no Object Storage</h1> 
                    <img src="https://objectstorage.us-ashburn-1.oraclecloud.com/n/id3kyspkytmr/b/workshops-materiais/o/site.gif"
            </center>   
        </body>
        </html>

    ```


4.	Una vez hecho esto, arrástrelo y suéltelo en el campo del depósito indicado y haga clic en **Upload**.

 ![imagen](../Lab5-ObjectStorage/Imagenes/Imagen20.png)

5.	Para el objeto, haga clic en el icono de tres puntos y haga clic en **View Object Details**.

![imagen](../Lab5-ObjectStorage/Imagenes/Imagen21.png) 

6. Haga clic en el URI indicado y verifique si el sitio está disponible. 

![imagen](../Lab5-ObjectStorage/Imagenes/Imagen22.png) 

![imagen](../Lab5-ObjectStorage/Imagenes/Imagen23.png) 

**Super! Continuemos con el siguiente laboratorio 🤩👉 [Laboratorio 6 - Load Balancer](https://github.com/kapvar9/oci-FastTrack-infraestructura/blob/main/Lab6-LoadBalancer/Readme.md)**
   
