---
title: Incluir un paquete NuGet en el proyecto
description: En este documento se explica cómo incluir un paquete NuGet en un proyecto de Xamarin. Le guía a lo largo del proceso de búsqueda y descarga de un paquete, además de presentar las características de integración del IDE.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.openlocfilehash: 4c945af52f4d19a1966809e905119d491cfc7432
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295753"
---
# <a name="include-a-nuget-package-in-your-project"></a>Incluir un paquete NuGet en el proyecto

NuGet es el administrador de paquetes más popular para el desarrollo de .NET y está integrado en Visual Studio para Mac y Visual Studio en Windows. Puede buscar y agregar paquetes a proyectos de Xamarin.iOS y Xamarin.Android mediante cualquier IDE.

En este artículo se explica cómo incluir un paquete NuGet en un proyecto y se muestra la cadena de herramientas que hace que el proceso se desarrolle sin problemas.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet en Visual Studio para Mac

Para mostrar la funcionalidad de los paquetes NuGet, primero se va a crear una nueva aplicación y se le va a agregar un paquete. Luego se tratan las características del IDE que ayudan a administrar paquetes.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo

En primer lugar, cree un proyecto denominado `HelloNuget` como se muestra a continuación. Este ejemplo muestra la plantilla de aplicación de vista única de iOS, aunque cualquier tipo de proyecto compatible funcionaría:

![Crear nuevo proyecto de iOS](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Adición de un paquete

Con el proyecto abierto en Visual Studio para Mac, haga clic con el botón derecho en la carpeta **Paquetes** del **Panel de solución** y seleccione **Agregar paquetes**:

![Acción contextual de adición de nuevo paquete NuGet](media/nuget-walkthrough-PackagesMenu.png)

Con esto se abre la ventana **Agregar paquetes**. Asegúrese de que la lista desplegable Origen esté establecida en `nuget.org`:

![Lista desplegable Origen](media/nuget-walkthrough-Source.png)

Cuando la ventana se abre, carga una lista de paquetes del origen de paquetes predeterminado: nuget.org. Los resultados iniciales presentan el siguiente aspecto:

![Lista de paquetes NuGet](media/nuget-walkthrough-AddPackages1.png)

Use el cuadro de búsqueda de la esquina superior derecha para buscar un paquete determinado, por ejemplo  `azure`. Cuando encuentre un paquete que quiera usar, selecciónelo y haga clic en el botón  **Agregar paquete**  para iniciar la instalación.

[Adición del paquete NuGet Azure](media/nuget-walkthrough-AddPackages2.png)

Una vez que el paquete se ha descargado, se agrega al proyecto. La solución cambia de este modo:

* El nodo **Referencias** contiene una lista de todos los ensamblados que forman parte de un paquete NuGet.
* El nodo **Paquetes** muestra cada paquete NuGet descargado. Puede actualizar esta lista o quitar un paquete de ella.
* Se agrega un archivo **packages.config** al proyecto. El IDE usa este archivo XML para realizar un seguimiento de a qué versiones del paquete se hace referencia en este proyecto. Este archivo no se debe editar manualmente, sino que debe mantenerse en el control de versiones. Tenga en cuenta que se puede usar un archivo project.json en lugar de un archivo packages.config. El archivo project.json es un nuevo formato de archivo de paquete presentado con NuGet 3 que admite la restauración transitiva. Puede ver información más detallada sobre project.json en la [documentación de NuGet](http://docs.microsoft.com/NuGet/Schema/Project-Json). Hay que agregar el archivo project.json manualmente y cerrar el proyecto y volverlo a abrir antes de usar el archivo project.json en Visual Studio para Mac.

## <a name="using-nuget-packages"></a>Uso de paquetes NuGet

Una vez agregado el paquete NuGet y actualizadas las referencias del proyecto, puede programar con las API como haría con cualquier referencia de proyecto.

Asegúrese de agregar cualquier directiva  `using`  necesaria a la parte superior del archivo:

```csharp
using Newtonsoft.Json;
```

La mayoría de los paquetes NuGet proporcionan información adicional, como un Léame o un vínculo de página de proyecto al origen de NuGet. Normalmente puede encontrar un vínculo a este en el texto del paquete en la página Agregar paquetes:

[Vínculo a la página Ver proyecto](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Actualizaciones de paquetes

Las actualizaciones de paquetes se pueden hacer todas a la vez, al hacer clic con el botón derecho en el nodo **Paquetes** o individualmente en cada componente.

Haga clic con el botón derecho en **Paquetes** para acceder al menú contextual:

![Menú Paquetes](media/nuget-walkthrough-PackagesMenu.png)

*   **Agregar paquetes**: abre la ventana para agregar más paquetes al proyecto.
*   **Actualizar**: comprueba el servidor de origen de cada paquete y descarga las versiones más recientes.
*   **Restaurar**: descarga todos los paquetes que faltan (sin actualizar los paquetes existentes a versiones más recientes).

Las opciones Actualizar y Restaurar también están disponibles en el nivel de solución y afectan a todos los proyectos de esta.

También puede hacer clic con el botón derecho en paquetes individuales para acceder a un menú contextual:

![Menú Paquetes](media/nuget-walkthrough-PackageMenu.png)

*   **Número de versión**: el número de versión es un elemento de menú deshabilitado que solo se proporciona con fines informativos.
*   **Actualizar**: comprueba el servidor de origen y descarga una versión más reciente (si la hubiera).
*   **Quitar**: quita el paquete de este proyecto y quita los ensamblados correspondientes de las referencias del proyecto.

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

## <a name="see-also"></a>Vea también

* [Instalación y uso de un paquete en Visual Studio (en Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)