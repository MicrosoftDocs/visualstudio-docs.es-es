---
title: "Tutorial de Azure para Visual Studio Tools para Unity: preparación| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: B921C2AC-B5D6-4B24-918E-511F83D57275
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 92f85e39d0f643e896457cae48ab10aa0446dfcd
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="prepare-the-development-environment"></a>Preparación del entorno de desarrollo

Hay algunos requisitos previos para poder usar el SDK del cliente móvil de Azure en Unity.

## <a name="download-and-install-unity-2017"></a>Descargar e instalar Unity 2017

Se necesita Unity 2017.1 o una versión posterior. Todos los planes de Unity son válidos para el tutorial, incluido el plan gratuito Personal. Descargue Unity en https://store.unity.com/.

## <a name="download-and-install-visual-studio-2017"></a>Descargar e instalar Visual Studio 2017

En el tutorial se debe usar Visual Studio 2017 15.3 o versiones posteriores, con la carga de trabajo Desarrollo de juego con Unity. Todas las ediciones de Visual Studio 2017 son válidas para el tutorial, incluida la edición gratuita Community.

1. Descargue Visual Studio 2017 en https://www.visualstudio.com/.

2. Instale Visual Studio 2017 y asegúrese de que la carga de trabajo **Desarrollo de juegos con Unity** está habilitada.

 ![Seleccionar la carga de trabajo de Unity](media/vstu_azure-prepare-dev-environment-image0.png)

 > [!NOTE]
 > Si Visual Studio 2017 ya está instalado, puede ver y modificar las cargas de trabajo ejecutando el instalador de Visual Studio.

## <a name="create-a-new-3d-unity-project"></a>Crear un proyecto 3D de Unity

Inicie Unity y cree un proyecto 3D.

![Crear un proyecto de Unity](media/vstu_azure-prepare-dev-environment-image1.png)

## <a name="set-the-script-editor-to-visual-studio-preview-2017"></a>Establecer el editor de scripts en Visual Studio Preview 2017

Es posible que ya tenga Visual Studio 2017 establecido como editor de scripts externos de Unity, pero es importante asegurarse de que la versión preliminar 15.3 está seleccionada.

1. En el menú **Editar** de Unity, elija **Editar > Preferencias...**.

  ![Menú para abrir las preferencias](media/vstu_azure-prepare-dev-environment-image1.2.png)

2. Cuando aparezca la ventana de preferencias de Unity, seleccione la pestaña **Herramientas externas**, situada a la izquierda.

3. En el menú desplegable **External Script Editor** (Editor de scripts externos), seleccione **Visual Studio 2017**.

  ![Establecer el editor de scripts externos](media/vstu_azure-prepare-dev-environment-image3.png)

## <a name="change-the-unity-scripting-runtime-to-net-46"></a>Cambiar el tiempo de ejecución de scripting de Unity en .NET 4.6
En el tutorial se debe usar .NET 4.6 para poder usar el SDK del cliente móvil de Azure y sus dependencias.

1. En el menú **Archivo** de Unity, elija **Archivo > Configuración de compilación...**

  ![Abrir Configuración de compilación](media/vstu_azure-prepare-dev-environment-image4.png)

2. Haga clic en el botón **Configuración del reproductor...**

  ![Abrir Configuración del reproductor](media/vstu_azure-prepare-dev-environment-image5.png)

3. Se abre Configuración del reproductor en la ventana Inspector de Unity. En el encabezado **Configuración**, haga clic en el menú desplegable **Scripting Runtime Version** (Versión en tiempo de ejecución de scripting) y seleccione **Experimental (.NET 4.6 Equivalent)** (Experimental [equivalente a .NET 4.6]). Aparecerá un cuadro de diálogo en el que se le indicará que reinicie Unity. Seleccione **Reiniciar**.

  ![Seleccionar .NET 4.6](media/vstu_azure-prepare-dev-environment-image6.png)

## <a name="add-a-reference-to-systemnethttpdll"></a>Agregar una referencia a System.Net.Http.dll

El tiempo de ejecución de scripting de Unity equivalente a .NET 4.6 permite usar el paquete System.Net.Http, necesario para el SDK del cliente móvil de Azure. El archivo DLL se incluye en Unity, aunque se debe agregar una referencia para poder usarlo.

1. En la ventana Proyecto del editor de Unity, **haga clic con el botón derecho** en la carpeta **Recursos** y seleccione **Mostrar en explorador**.

  ![Carpeta Mostrar recursos en el Explorador](media/vstu_azure-prepare-dev-environment-image7.png)

2. En la ventana del explorador que aparece, haga doble clic en el directorio **Recursos** para abrirlo.

3. En el directorio Recursos, **haga clic con el botón derecho** y seleccione **Nuevo > Documento de texto**.

4. Abra el nuevo documento de texto en un editor de texto y agregue la línea: `-r:System.Net.Http.dll`

5. Guarde el documento y ciérrelo.

4. Cambie el nombre del nuevo documento de texto por "**mcs.rsp**" y asegúrese de eliminar la extensión de archivo .txt.

  * Si tiene extensiones de archivo ocultas, deberá cambiar las opciones de vista de carpeta para mostrarlas.
  * Abra el menú Inicio y escriba "opciones de carpeta" para efectuar la búsqueda. Seleccione "**Opciones del Explorador de archivos**".
  * Seleccione la pestaña **Vista** y, en la configuración avanzada, asegúrese de que la opción "**Ocultar las extensiones de los tipos de archivo conocidos**" está desactivada.

    ![Carpeta Mostrar recursos en el Explorador](media/vstu_azure-prepare-dev-environment-image8.png)

Después de haber seguido estos pasos, debería tener un archivo denominado **mcs.rsp** con la línea `r:System.Net.Http.dll` en el directorio raíz **Recursos** del proyecto de Unity.

>[!NOTE]
> La funcionalidad de referencia requiere Visual Studio Tools para Unity 3.3 y versiones posteriores, que se incluye en la carga de trabajo de Visual Studio 15.3 + Unity. Si este paso no funciona, asegúrese de que tiene instalada la versión correcta de VSTU.

## <a name="add-the-newtonsoftjson-nuget-package-to-your-project"></a>Agregar el paquete Newtonsoft.Json de NuGet al proyecto

El SDK del cliente móvil de Azure requiere el paquete Newtonsoft.Json. Por desgracia, Unity no es compatible con NuGet. Si abre un proyecto Unity en Visual Studio y agrega un paquete con NuGet, Unity lo borrará la próxima vez que abra el proyecto en el editor de Unity, pero los paquetes de NuGet se pueden agregar manualmente a un proyecto de Unity.

1. Cree una carpeta en el directorio Recursos del proyecto Unity denominada "**Paquetes de NuGet**". Este paso es solo a efectos de organización.

2. Vaya a https://www.nuget.org/packages/Newtonsoft.Json/ y haga clic en el botón **Manual Download** (Descarga manual). Descargue el archivo .nupkg.

  ![Carpeta Mostrar recursos en el Explorador](media/vstu_azure-prepare-dev-environment-image9.png)

3. Busque el archivo recién descargado y cambie la extensión de .nupkg a **.zip**. Debería poder ver y extraer los archivos incluidos como cualquier otro archivo zip.

4. Abra o extraiga el directorio zip y vaya a **\lib\net45**.

5. Copie el archivo **Newtonsoft.Json.dll** en el directorio **Assets\Paquetes de NuGet** del proyecto de Unity.

## <a name="add-the-azure-mobile-client-sdk-nuget-package-to-your-project"></a>Agregar al proyecto el paquete de NuGet del SDK del cliente móvil de Azure

El SDK del cliente móvil de Azure contiene funciones que permiten leer y escribir fácilmente en las tablas fáciles de Azure.

1. Vaya a https://www.nuget.org/packages/Microsoft.Azure.Mobile.Client/ y haga clic en el botón **Manual Download** (Descarga manual). Descargue el archivo .nupkg.

2. Busque el archivo recién descargado y cambie la extensión de .nupkg a **.zip**. Debería poder ver y extraer los archivos incluidos como cualquier otro archivo zip.

3. Abra o extraiga el directorio zip y vaya a **\lib\net45**.

4. Copie el archivo **Microsoft.Azure.Mobile.Client.dll** en el directorio **Assets\Paquetes de NuGet** del proyecto de Unity.

>[!WARNING]
> Después de haber seguido estos pasos, asegúrese de reiniciar Unity y Visual Studio. Si no lo hace, InteliSense podría no reconocer los paquetes recién agregados.

## <a name="conclusion"></a>Conclusión

Después de haber seguido estos pasos, se debe configurar el proyecto de Unity para poder usar el SDK del cliente móvil de Azure. Para probar el entorno de desarrollo, cree un script de C# en el proyecto de Unity, ábralo en Visual Studio y escriba las siguientes instrucciones Using en la parte superior:
```
using System.Net.Http;
using Newtonsoft.Json;
using Microsoft.WindowsAzure.MobileServices;
```

Si InteliSense detecta estas instrucciones Using, quiere decir que el programa de instalación se completó correctamente. Si hay algún error o InteliSense no reconoce estos paquetes, pruebe a reiniciar Unity y Visual Studio. Si aun así no funciona, revise los pasos anteriores.

## <a name="next-step"></a>Paso siguiente

* [Creación de clases de modelo de datos](visual-studio-tools-for-unity-azure-data.md)
