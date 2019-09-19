---
title: Incluir un paquete NuGet en el proyecto
description: En este documento se explica cómo incluir un paquete NuGet en un proyecto mediante Visual Studio para Mac. Le guía a lo largo del proceso de búsqueda y descarga de un paquete, además de presentar las características de integración del IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/17/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 22b2e07509403d8e19e3a3e920d45b064c2e51c0
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079532"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Instalación y administración de paquetes NuGet en Visual Studio para Mac

La interfaz de usuario del Administrador de paquetes NuGet en Visual Studio para Mac le permite instalar, desinstalar y actualizar fácilmente paquetes NuGet en proyectos y soluciones. Puede buscar y agregar paquetes a los proyectos de .NET Core, ASP.NET Core y Xamarin.

En este artículo se explica cómo incluir un paquete NuGet en un proyecto y se muestra la cadena de herramientas que hace que el proceso se desarrolle sin problemas.

Para obtener una introducción al uso de NuGet en Visual Studio para Mac, consulte [Inicio rápido: instalación y uso de un paquete en Visual Studio para Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Búsqueda e instalación de un paquete

1. Con un proyecto abierto en Visual Studio para Mac, haga clic con el botón derecho en la carpeta **Dependencias** (carpeta **Paquetes** si se usa un proyecto de Xamarin) del **Panel de solución** y seleccione **Agregar paquetes**.

    ![Acción contextual de adición de nuevo paquete NuGet](media/nuget-walkthrough-PackagesMenu.png)

2. Con esto se abre la ventana **Agregar paquetes**. Asegúrese de que la lista desplegable Origen de la esquina superior izquierda del cuadro de diálogo está establecida en `nuget.org`.

    ![Lista de paquetes NuGet](media/nuget-walkthrough-AddPackages1.png)

3. Use el cuadro de búsqueda de la esquina superior derecha para buscar un paquete determinado, por ejemplo `EntityFramework`. Si encuentra un paquete que quiera usar, selecciónelo y haga clic en el botón **Agregar paquete** para iniciar la instalación.

    ![Adición de paquete NuGet de Azure](media/nuget-walkthrough-AddPackages2.png)

4. Una vez que el paquete se ha descargado, se agrega al proyecto. La solución cambiará en función del tipo de proyecto que esté editando:

    **Proyectos de Xamarin**
    * El nodo **Referencias** contiene una lista de todos los ensamblados que forman parte de un paquete NuGet.
    * El nodo **Paquetes** muestra cada paquete NuGet descargado. Puede actualizar esta lista o quitar un paquete de ella.
    
    **Proyectos de .NET Core**

    El nodo **Dependencias > NuGet** muestra cada paquete NuGet descargado. Puede actualizar esta lista o quitar un paquete de ella.

## <a name="using-nuget-packages"></a>Uso de paquetes NuGet

Una vez agregado el paquete NuGet y actualizadas las referencias del proyecto, puede programar con las API como haría con cualquier referencia de proyecto.

Asegúrese de agregar cualquier directiva `using` necesaria a la parte superior del archivo:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Actualización de paquetes

Las actualizaciones de paquetes se pueden hacer todas a la vez, al hacer clic con el botón derecho en el nodo **Dependencias** (o el nodo **Paquetes** para proyectos de Xamarin) o individualmente en cada componente.

Haga clic con el botón derecho en **Dependencias** para acceder al menú contextual:

![Menú Paquetes](media/nuget-walkthrough-PackagesMenu.png)

* **Administrar paquetes NuGet**: abre la ventana para agregar más paquetes al proyecto.
* **Actualizar**: comprueba el servidor de origen de cada paquete y descarga las versiones más recientes.
* **Restaurar**: descarga todos los paquetes que faltan (sin actualizar los paquetes existentes a versiones más recientes).

Las opciones Actualizar y Restaurar también están disponibles en el nivel de solución y afectan a todos los proyectos de esta.

En el Panel de solución, puede ver la versión de un paquete que está instalada actualmente y hacer clic con el botón derecho en el paquete que se va a actualizar.

![Menú Paquetes con las opciones para Actualizar, Quitar y Refrescar.](media/nuget-walkthrough-PackageMenu.png)

También verá una notificación junto al nombre del paquete cuando haya disponible una nueva versión de un paquete, de tal forma que pueda decidir si quiere actualizarlo.

![Notificación que se muestra cuando hay disponible una nueva versión del paquete.](media/nuget-walkthrough-package-update-available.png)

En el menú que se muestra, tiene dos opciones:

* **Actualizar**: comprueba el servidor de origen y descarga una versión más reciente (si la hubiera).
* **Quitar**: quita el paquete de este proyecto y quita los ensamblados correspondientes de las referencias del proyecto.

## <a name="adding-package-sources"></a>Adición de orígenes de paquetes

Los paquetes disponibles para instalar se recuperan inicialmente de nuget.org. Pero puede agregar otras ubicaciones de paquetes a Visual Studio para Mac. Esto puede ser útil para probar los paquetes NuGet propios en desarrollo o para usar un servidor NuGet privado dentro de la empresa u organización.

En Visual Studio para Mac, vaya a **Visual Studio > Preferencias > NuGet > Orígenes** para ver y editar la lista de orígenes de paquetes. Tenga en cuenta que los orígenes pueden ser un servidor remoto (especificado por una dirección URL) o un directorio local.

![Orígenes de paquetes](media/nuget-walkthrough-PackageSource.png)

Haga clic en **Agregar** para configurar un nuevo origen. Escriba un nombre descriptivo y la dirección URL (o ruta de acceso de archivo) al origen del paquete. Si el origen es un servidor web seguro, escriba también el nombre de usuario y la contraseña, de lo contrario, deje en blanco estas entradas:

![Adición de orígenes de paquetes](media/nuget-walkthrough-PackageSource2.png)

Al buscar paquetes se pueden seleccionar orígenes diferentes:

![Adición de orígenes de paquetes](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Control de versiones

En la documentación de NuGet se trata el [uso de NuGet sin confirmar paquetes en el control de código fuente](/nuget/consume-packages/packages-and-source-control). Si prefiere no almacenar archivos binarios ni información sin usar en el control de código fuente, puede configurar Visual Studio para Mac de modo que restaure automáticamente los paquetes desde el servidor. Esto significa que cuando un desarrollador recupera el proyecto del control de código fuente por primera vez, Visual Studio para Mac descarga e instala automáticamente los paquetes necesarios.

![Restauración automática de paquetes](media/nuget-walkthrough-AutoRestore.png)

Consulte la documentación del control de origen de su propiedad para obtener detalles sobre cómo excluir el directorio `packages` del seguimiento.

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Vea también

* [Inicio rápido: Instalación y uso de un paquete en Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
