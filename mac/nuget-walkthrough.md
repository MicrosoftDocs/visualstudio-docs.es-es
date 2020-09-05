---
title: Incluir un paquete NuGet en el proyecto
description: En este documento se explica cómo incluir un paquete NuGet en un proyecto mediante Visual Studio para Mac. Le guía a lo largo del proceso de búsqueda y descarga de un paquete, además de presentar las características de integración del IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "74127202"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Instalación y administración de paquetes NuGet en Visual Studio para Mac

La interfaz de usuario del Administrador de paquetes NuGet en Visual Studio para Mac le permite instalar, desinstalar y actualizar fácilmente paquetes NuGet en proyectos y soluciones. Puede buscar y agregar paquetes a los proyectos de .NET Core, ASP.NET Core y Xamarin.

En este artículo se explica cómo incluir un paquete NuGet en un proyecto y se muestra la cadena de herramientas que hace que el proceso se desarrolle sin problemas.

Para obtener una introducción al uso de NuGet en Visual Studio para Mac, consulte [Inicio rápido: instalación y uso de un paquete en Visual Studio para Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Búsqueda e instalación de un paquete

1. Con un proyecto abierto en Visual Studio para Mac, haga clic con el botón derecho en la carpeta **Dependencias** (carpeta **Paquetes** si usa un proyecto de Xamarin) del **Panel de solución** y seleccione **Administrar paquetes NuGet…**

    ![Acción contextual de adición de nuevo paquete NuGet](media/nuget-walkthrough-packages-menu.png)

2. Se abre la ventana **Administrar paquetes NuGet**. Asegúrese de que la lista desplegable Origen de la esquina superior izquierda del cuadro de diálogo esté establecida en `nuget.org`, de modo que pueda realizar la búsqueda en el repositorio de paquetes central de NuGet.

    ![Lista de paquetes NuGet](media/nuget-walkthrough-add-packages1.png)

3. Use el cuadro de búsqueda de la esquina superior derecha para buscar un paquete determinado, por ejemplo `EntityFramework`. Si encuentra un paquete que quiera usar, selecciónelo y haga clic en el botón **Agregar paquete** para iniciar la instalación.

    ![Adición del paquete NuGet de EntityFramework](media/nuget-walkthrough-add-packages2.png)

4. Una vez que el paquete se ha descargado, se agrega al proyecto. La solución cambiará en función del tipo de proyecto que esté editando:

    **Proyectos de Xamarin**
    * El nodo **Referencias** contiene una lista de todos los ensamblados que forman parte de un paquete NuGet.
    * El nodo **Paquetes** muestra cada paquete NuGet descargado. Puede actualizar esta lista o quitar un paquete de ella.
    
    **Proyectos de .NET Core**

    * El nodo **Dependencias > NuGet** muestra cada paquete NuGet descargado. Puede actualizar esta lista o quitar un paquete de ella.

## <a name="using-nuget-packages"></a>Uso de paquetes NuGet

Una vez agregado el paquete NuGet y actualizadas las referencias del proyecto, puede programar con las API como haría con cualquier referencia de proyecto.

Asegúrese de agregar cualquier directiva `using` necesaria a la parte superior del archivo:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Actualización de paquetes

Las actualizaciones de paquetes se pueden hacer todas a la vez, al hacer clic con el botón derecho en el nodo **Dependencias** (nodo **Paquetes** para proyectos de Xamarin) o individualmente en cada paquete. Cuando hay disponible una nueva versión de un paquete NuGet, aparece el icono de actualización ![flecha hacia arriba con círculo](media/nuget-walkthrough-update-icon.png).

Haga clic con el botón derecho en **Dependencias** para acceder al menú contextual y elija **Actualizar** para actualizar todos los paquetes:

![Menú Paquetes](media/nuget-walkthrough-packages-menu-update.png)

* **Administrar paquetes NuGet**: abre la ventana para agregar más paquetes al proyecto.
* **Actualizar**: comprueba el servidor de origen de cada paquete y descarga las versiones más recientes.
* **Restaurar**: descarga todos los paquetes que faltan (sin actualizar los paquetes existentes a versiones más recientes).

Las opciones Actualizar y Restaurar también están disponibles en el nivel de solución y afectan a todos los proyectos de esta.

### <a name="locating-outdated-packages"></a>Búsqueda de paquetes obsoletos
En el Panel de solución, puede ver la versión de un paquete que está instalada actualmente y hacer clic con el botón derecho en el paquete que se va a actualizar.

![Menú Paquetes con las opciones para Actualizar, Quitar y Refrescar.](media/nuget-walkthrough-PackageMenu.png)

También verá una notificación junto al nombre del paquete cuando haya disponible una nueva versión de un paquete, de tal forma que pueda decidir si quiere actualizarlo.

![Notificación que se muestra cuando hay disponible una nueva versión del paquete.](media/nuget-walkthrough-package-update-available.png)

En el menú que se muestra, tiene dos opciones:

* **Actualizar**: comprueba el servidor de origen y descarga una versión más reciente (si la hubiera).
* **Quitar**: quita el paquete de este proyecto y quita los ensamblados correspondientes de las referencias del proyecto.

## <a name="manage-packages-for-the-solution"></a>Administración de paquetes para la solución

Administrar los paquetes de una solución es un medio cómodo para trabajar con varios proyectos a la vez.

1. Haga clic con el botón derecho en la solución y seleccione **Administrar paquetes NuGet...**:

    ![Administrar paquetes NuGet para la solución](media/nuget-walkthrough-manage-packages-solution.png)

1. Cuando administra paquetes para la solución, la interfaz de usuario le permite seleccionar los proyectos que se ven afectados por las operaciones:

    ![Selector de proyectos al administrar los paquetes para la solución](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Pestaña Consolidar

Al trabajar en una solución con varios proyectos, un procedimiento recomendado es asegurarse de que cualquier lugar en el que se use el mismo paquete NuGet en cada proyecto esté usando también el mismo número de versión de ese paquete. Visual Studio para Mac facilita esta tarea, ya que proporciona la pestaña **Consolidado** en la interfaz de usuario del Administrador de paquetes a la hora de administrar paquetes para una solución. Con esta pestaña, puede ver fácilmente dónde se usan los paquetes con números de versión diferentes en distintos proyectos de la solución:

![Pestaña Consolidar de la interfaz de usuario del Administrador de paquetes](media/nuget-walkthrough-consolidate-tab.png)

En este ejemplo, el proyecto NuGetDemo usa Microsoft.EntityFrameworkCore 2.20, mientras que NuGetDemo.Shared usa Microsoft.EntityFrameworkCore 2.2.6. Para consolidar las versiones de los paquetes, haga lo siguiente:

- Seleccione los proyectos que se van a actualizar en la lista de proyectos.
- Seleccione la versión que usará en todos los proyectos de la lista **Nueva versión**, como Microsoft.EntityFrameworkCore 3.0.0.
- Seleccione el botón **Consolidar paquete**.

El Administrador de paquetes instala la versión de paquete seleccionada en todos los proyectos seleccionados, después de lo cual el paquete deja de aparecer en la pestaña **Consolidar**.

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
