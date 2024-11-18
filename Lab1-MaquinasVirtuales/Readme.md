# Creación de maquinas virtuales

Esta sección contiene 2 partes:
- [Máquinas Virtuales](#aprendamos-un-poco-sobre-las-máquinas-virtuales)
- [Laboratorio 3](#laboratorio-3-creación-de-máquinas-virtuales)

## Aprendamos un poco sobre las máquinas virtuales 

Oracle Cloud Infrastructure permite aprovisionar y gestionar hosts de cómputo conocidos como instancias. Puedes crear instancias según sea necesario para satisfacer tus requisitos de cómputo y aplicaciones. Después de crear una instancia, puedes acceder a ella de forma segura desde tu computadora, reiniciarla, adjuntar y desvincular volúmenes y cerrarla cuando ya no la necesites. Esto proporciona flexibilidad y escalabilidad para satisfacer las necesidades de tu infraestructura de TI en la nube.

Para saber más, puedes consultar la documentación de OCI 🤓➡️ https://docs.oracle.com/en-us/iaas/Content/Compute/Concepts/computeoverview.htm

## Laboratorio 3: Creación de máquinas virtuales

En este laboratorio, aprenderás a crear 2 máquinas virtuales Linux.

_**Tiempo estimado para el laboratorio**_: 35 minutos

Objetivos:
- Crear un par de claves SSH en OCI Cloud Shell
- Crear 2 máquinas virtuales (VM) Linux
- Acceder a las instancias

**Cada máquina virtual debe estar en un AD diferente**. Para ellos seguiremos los siguientes pasos:
- [Paso 1: Crear un par de llaves SSH](#paso-1-crear-un-par-de-llaves-ssh)
- [Paso 2: Crear 2 máquinas virtuales Oracle Linux](#paso-2-crear-2-máquinas-virtuales-oracle-linux)
- [Paso 3: Acceder a la VM por el terminal](#paso-3-acceder-a-la-vm-por-el-terminal)

### Paso 1: Crear un par de llaves SSH

1. Abrimos el escritorio remoto y el terminal 

  ![imagen](../PrimerosPasos/imagenes/paso23.png)

2. Para crear el par de llaves usamos el comando:

   ```
   ssh-keygen -t rsa
   ```
   - Mantenga el nombre original de la llave (id_rsa) aprentando enter
   - El campo "Key Passphrase" es opcional

   ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-1.png)

3. Para ver el contenido de la llave pública, ejecuta este comando:
   
   ```
   cat ~/.ssh/id_rsa.pub
   ```
  > **Nota:** Si no sabes la combinación de teclas para el símbolo "~" (virgulilla), busca el símbolo y copialo en el área de transferencia del Escritorio Remoto. Luego de ello, pégalo dentro del terminal usando _clic derecho + pegar_. Puedes hacer esto para facilitar el copiado/pegado de texto entre tu escritorio y el escritorio remoto.

   ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-3.png)

  * Selecciona y copia el contenido de la llave. Usaremos esto para la creación de las máquinas virtuales. Recuerda copiar el texto en el área de transferencia del Escritorio Remoto
    
    ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-2.png)

  _Para la creación de la VM, usaremos una llave pública y para la conexión, usaremos la llave privada_

   ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-4.png)
     
### Paso 2: Crear 2 máquinas virtuales Oracle Linux

1. En el menú 🍔, vamos a Compute ➡️ Instances

   ![imagen](../Lab1-Compartimentos/Imagenes/lab1-5.png)
   
2. En "Compute", haz clic en _"Create Instance"_, recuerda verificar que te encuentras en tu compartment correspondiente
   
   ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-5.png)

    Estos serán los datos de tu instancia:
    * Nombre de tu instancia: VM-OracleLinux-AD2
    * Dominio de Disponibilidad: AD 2
    * Sistema Operativo: Oracle Linux 7.9
    * Tipo de Instancia: Máquina Virtual
    * Forma de la Instancia: AMD VM.Standard.E4.Flex
    * Elija el Archivo de Clave SSH: Inserta el archivo de clave pública SSH (.pub)
    * Compartimento de la Red de Nube Virtual: "Tu Compartimento"
    * Red de Nube Virtual: "Tu VCN"
    * Compartimento de Subred: "Tu Compartimento" (Creado por defecto en el ambiente)
    * Subred: Subred Pública

     Llena los datos según lo indicado. **Recuerda que ya tienes un compartment creado por defecto. Debes elegir ese** 🤓☝️
   
      ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-7.png)
  
      > **Nota:** Recuerda que tus máquinas virtuales deben estar en ADs diferentes. Hay una máquina creada por defecto con el ambiente y que se encuentra en un AD en específico. Las nuevas máquinas deben ser creadas en los otros ADs que quedan
      ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-6.png)
      > _En el ejemplo, la máquina por defecto se encuentra en el AD1 así que las 2 nuevas máquinas deberán ser creadas en el AD 2 y el AD 3_

3. Elige la imagen y el shape de tu MV. Haz clic en _"Change Image"_ para cambiar la imagen y en _"Change shape"_ para cambiar el shape

   ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-8.png)

   - Cambiar imagen
     
     ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-9.png)

    - Cambiar shape

     ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-10.png)
     ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-11.png)

   _Resultado_

    ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-12.png)

4. Selecciona la VCN y la subnet pública creadas por defecto, y eliga la opción de _"Asignar una dirección IPv4 pública"_

   ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-13.png)

5. Colocamos la llave pública SSH creada en el paso 3 y clic en _"Create"_

   ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-14.png)

  Tu instancia tomará unos minutos en crearse. Si esta todo OK🤞, quedará como la imagen ⤵️
  
  ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-15.png)

6. Realizamos los mismos pasos para crear la MV2. La crearemos en el AD restante.
   Estos serán los datos de tu instancia:
    * Nombre de tu instancia: VM-OracleLinux-AD3
    * Dominio de Disponibilidad: AD 3
    * Sistema Operativo: Oracle Linux 7.9
    * Tipo de Instancia: Máquina Virtual
    * Forma de la Instancia: AMD VM.Standard.E4.Flex
    * Elija el Archivo de Clave SSH: Inserta el archivo de clave pública SSH (.pub)
    * Compartimento de la Red de Nube Virtual: "Tu Compartimento"
    * Red de Nube Virtual: "Tu VCN"
    * Compartimento de Subred: "Tu Compartimento"
    * Subred: Subred Pública

  ### Paso 3: Acceder a la VM por el terminal

  1. Copiamos la IP privada de una nuestras instancias
     
     ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-18.png)

  2. Volvemos al Escritorio Remoto, y en el terminal, hacemos la conexión con la máquina creada usando el siguiente comando

     ```
     ssh opc@<ip privado da VM>
     ```

     * El usuario por defecto de las instancias Linux es OPC

     ![imagen](../Lab3-MaquinasVirtuales/imagenes/lab3-17.png)

     **Super! Continuemos con el siguiente laboratorio 🤩👉 [Laboratorio 4 - Block Volume](https://github.com/kapvar9/oci-FastTrack-infraestructura/blob/main/Lab5-ObjectStorage/Readme.md)**
   
   
