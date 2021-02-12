---
title: Actualización de Visual Studio con un diseño sin conexión mínimo
description: Obtenga información sobre cómo actualizar Visual Studio con un diseño sin conexión mínimo.
ms.date: 07/21/2020
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 199771b1cda2049d6508832d7d2264558104a566
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935708"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Actualización de Visual Studio con un diseño sin conexión mínimo

En el caso de los equipos que no están conectados a Internet, la creación de un diseño mínimo es la manera más fácil y rápida de actualizar las instancias de Visual Studio sin conexión.

La herramienta de diseño mínimo genera un diseño adaptado específicamente a las necesidades del equipo. Los administradores de empresa pueden usar esta herramienta para crear diseños de actualización para la mayoría de las versiones de Visual Studio 2017 y 2019. A diferencia de un diseño de Visual Studio completo, uno mínimo solo contiene los paquetes actualizados, por lo que siempre es más pequeño, y se genera e implementa más rápido. Puede minimizar aún más el tamaño del diseño de actualización especificando solo los idiomas, las cargas de trabajo y los componentes que quiera.

## <a name="how-to-generate-a-minimal-layout"></a>Procedimiento para generar un diseño mínimo

> [!IMPORTANT]
> En estas instrucciones se da por hecho que ya ha creado y usado diseños. Para obtener más información sobre cómo hacerlo, vea la página [Actualización de una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md).
>
> Para comprender mejor el ciclo de vida de Visual Studio, vea la página [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing).
>

Esta herramienta permite crear diseños de actualización para Visual Studio 2017 (15.9) y versiones posteriores. El diseño se puede implementar en equipos de red o sin conexión para actualizar instancias de Visual Studio. Durante la [creación del diseño normal](update-a-network-installation-of-visual-studio.md), se descargan todos los paquetes de la versión en cuestión. La creación del diseño normal es necesaria para reparar y desinstalar instancias de Visual Studio, así como para llevar a cabo otras operaciones estándar relacionadas con estas. En el caso del diseño mínimo, solo se descargan los paquetes actualizados, por lo que es más pequeño y se copia más fácilmente en máquinas sin conexión.

### <a name="installing-the-minimal-layout-tool"></a>Instalación de la herramienta de diseño mínimo
 
 1. En primer lugar, descargue la herramienta de diseño mínimo, disponible [aquí](https://aka.ms/vs/installer/minimallayout). Asegúrese de elegir **Guardar** cuando se le solicite y, después, seleccione **Ejecutar**.

     ![Herramienta para guardar el diseño mínimo](media/save-minimal-layout.png)

 2. A continuación, acepte la solicitud de Control de cuentas de usuario haciendo clic en **Sí**.

     ![Aceptación de Control de cuentas de usuario](media/accept-user-account-control.png)

 3. La herramienta de diseño mínimo se instalará en `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout`.

### <a name="how-to-use-the-minimal-layout-tool"></a>Procedimiento para usar la herramienta de diseño mínimo

`MinimalLayout.exe` usa los comandos y opciones siguientes para generar el diseño. Se requiere al menos un comando para ejecutar la herramienta. A continuación se muestra cómo debe ejecutar la herramienta:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Comandos
* **Vista previa**: use este comando para obtener una vista previa de cuántos paquetes se descargarán y el espacio total que se usará para crear el diseño. 
* **Generar**: use este comando para generar el diseño mínimo a fin de actualizar Visual Studio.
* **Regenerar**: use este comando para volver a generar un diseño mediante un archivo de respuesta de diseño mínimo existente. Cada diseño mínimo genera un archivo de respuesta `MinimalLayout.json` que contiene los parámetros de entrada de diseño mínimo originales. Puede usar el comando **Regenerar** y un archivo de respuesta `MinimalLayout.json` para volver a generar el diseño mínimo. Esto resulta útil si quiere crear un diseño mínimo para una nueva actualización de Visual Studio que se base en el archivo de respuesta de diseño mínimo anterior.

   Para este comando, se requiere una ruta de acceso de archivo `MinimalLayout.json` de un diseño ya generado. 

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **Comprobar**: use este comando para determinar si la carpeta de diseño está dañada.
* **Corregir**: use este comando para corregir una carpeta de diseño dañada, lo cual incluye el reemplazo de los paquetes que falten en la carpeta del diseño.

::: moniker range="vs-2019"

#### <a name="options"></a>Opciones 

|Opciones    |Descripción    |Obligatorio/opcional |Ejemplo |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt;dir&gt; |Especifica un directorio en el que se creará un diseño sin conexión mínimo.       |Obligatorio        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt;version&gt;|El diseño mínimo sin conexión se generará a partir de esta versión.   |Obligatorio|--baseVersion 16.4.0 |
|--targetVersion &lt;version&gt;|El diseño mínimo sin conexión se generará hasta esta versión (incluida).|Obligatorio|--targetVersion 16.4.4|
|--languages    |Especifica los idiomas que se incluirán en el diseño mínimo sin conexión. Se pueden especificar varios valores separados por espacios.    |Obligatorio    |--languages en-US fr-FR |
|--productId &lt;id&gt;    |Identificador del producto a partir del que se generará el diseño mínimo sin conexión. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Obligatorio|--productId Microsoft.VisualStudio.Product.Enterprise |
|--filePath    |Ruta de acceso del archivo MinimalLayout.json de un diseño ya creado. Esta opción solo se utiliza con el comando Regenerar.     |Obligatorio para el comando Regenerar    |--filePath C:\VSLayout\minimalLayout.json <br><br> **Tenga en cuenta que el comando Regenerar solo toma --filePath como opción.** |
|--add &lt;(al menos un id. de componente o carga de trabajo)&gt;    |Especifica al menos un identificador de componente o carga de trabajo para agregar. Puede agregar componentes adicionales de forma global usando --includeRecommended o <br> --includeOptional. Se pueden especificar varios id. de componente o carga de trabajo separados por un espacio.    |Optional    |--add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio |
|--includeRecommended    |incluye los componentes recomendados para cualquier carga de trabajo que se instale, pero no los componentes recomendados.    |Optional    |Para una carga de trabajo específica: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Para la aplicación a todas las cargas de trabajo: --includeRecommended |
|--includeOptional |Incluye los componentes opcionales para cualquier carga de trabajo que se instale, pero no los componentes recomendados.    |Optional    |Para una carga de trabajo específica: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Para la aplicación a todas las cargas de trabajo: --includeOptional |

::: moniker-end

::: moniker range="vs-2017"

#### <a name="options"></a>Opciones 

|Opciones    |Descripción    |Obligatorio/opcional |Ejemplo |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt;dir&gt; |Especifica un directorio en el que se creará un diseño sin conexión mínimo.       |Obligatorio        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt;version&gt;|El diseño mínimo sin conexión se generará a partir de esta versión.   |Obligatorio|--baseVersion 15.0.0 |
|--targetVersion &lt;version&gt;|El diseño mínimo sin conexión se generará hasta esta versión (incluida).|Obligatorio|--targetVersion 15.9.31|
|--languages    |Especifica los idiomas que se incluirán en el diseño mínimo sin conexión. Se pueden especificar varios valores separados por espacios.    |Obligatorio    |--languages en-US fr-FR |
|--productId &lt;id&gt;    |Identificador del producto a partir del que se generará el diseño mínimo sin conexión. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Obligatorio|--productId Microsoft.VisualStudio.Product.Enterprise |
|--filePath    |Ruta de acceso del archivo MinimalLayout.json de un diseño ya creado. Esta opción solo se utiliza con el comando Regenerar.     |Obligatorio para el comando Regenerar    |--filePath C:\VSLayout\minimalLayout.json <br><br> **Tenga en cuenta que el comando Regenerar solo toma --filePath como opción.** |
|--add &lt;(al menos un id. de componente o carga de trabajo)&gt;    |Especifica al menos un identificador de componente o carga de trabajo para agregar. Puede agregar componentes adicionales de forma global usando --includeRecommended o <br> --includeOptional. Se pueden especificar varios id. de componente o carga de trabajo separados por un espacio.    |Optional    |--add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio |
|--includeRecommended    |incluye los componentes recomendados para cualquier carga de trabajo que se instale, pero no los componentes recomendados.    |Optional    |Para una carga de trabajo específica: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Para la aplicación a todas las cargas de trabajo: --includeRecommended |
|--includeOptional |Incluye los componentes opcionales para cualquier carga de trabajo que se instale, pero no los componentes recomendados.    |Optional    |Para una carga de trabajo específica: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Para la aplicación a todas las cargas de trabajo: --includeOptional |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Generación de un diseño mínimo

> [!IMPORTANT]
>  En estas instrucciones se da por hecho que ya se ha creado previamente un diseño de instalación de red. Para más información sobre cómo hacerlo, vea la página [Creación de una instalación de red de Visual Studio](create-a-network-installation-of-visual-studio.md).

Cree un diseño mínimo para el intervalo de versiones especificado mediante el comando **Regenerar**. También necesitará conocer el id. de producto, los idiomas y las cargas de trabajo específicas que sean necesarias. Este diseño mínimo actualizará cualquier instancia de Visual Studio de la versión base a la de destino (incluida).

Antes de crear el diseño, puede averiguar el tamaño total de la descarga y el número de paquetes incluidos mediante el comando **Vista previa**. Este comando toma las mismas opciones que el comando **Regenerar**, y los detalles se escriben en la consola.

Veamos algunos ejemplos de cómo obtener una vista previa de un diseño mínimo, además de cómo generarlo y volver a generarlo:

::: moniker range="vs-2019"

- En primer lugar, a continuación se muestra un ejemplo de cómo obtener una vista previa de un diseño para Visual Studio Enterprise en las versiones de 16.4.0 a 16.4.4 (solo para inglés).

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Aquí se muestra cómo generar el mismo diseño con una carga de trabajo.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- Y aquí se muestra cómo volver a generar un diseño sin conexión mínimo mediante un archivo de respuesta existente. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Un par de otros ejemplos usando el comando **Regenerar**:

- Aquí se muestra cómo agregar una carga de trabajo adicional e incluir solo los paquetes recomendados. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Y, por último, aquí se muestra cómo incluir varios idiomas en el diseño mínimo. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

::: moniker range="vs-2017"

- En primer lugar, a continuación se muestra un ejemplo de cómo obtener una vista previa de un diseño para Visual Studio Enterprise en las versiones de 15.0.0 a 15.9.31 (solo para inglés).

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
    ```

- Aquí se muestra cómo generar el mismo diseño con una carga de trabajo.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- Y aquí se muestra cómo volver a generar un diseño sin conexión mínimo mediante un archivo de respuesta existente. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Un par de otros ejemplos usando el comando **Regenerar**:

- Aquí se muestra cómo agregar una carga de trabajo adicional e incluir solo los paquetes recomendados. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Y, por último, aquí se muestra cómo incluir varios idiomas en el diseño mínimo. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Procedimiento para mantener un diseño mínimo

Use los comandos **Comprobar** y **Corregir** para mantener el diseño mínimo después de su creación. El comando **Comprobar** permite determinar si hay paquetes dañados o que falten en el diseño mínimo. Si encuentra algún problema después de ejecutar el comando **Comprobar**, use el comando **Corregir** para corregir los paquetes que falten o estén dañados.

- Aquí se muestra cómo comprobar si un diseño tiene paquetes dañados o que falten: 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- Y aquí se muestra cómo corregir este diseño:

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> Este diseño no se puede usar para reparar una instalación de Visual Studio. Para reparar una instancia existente de Visual Studio, vea [Reparación de Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Procedimiento para usar un diseño sin conexión mínimo para actualizar una instalación existente de Visual Studio

Después de generar un diseño mínimo, puede copiar toda la carpeta de diseño mínimo en un equipo cliente. Esto es necesario si el equipo no puede acceder a la carpeta de diseño mínimo en su ubicación original.

Navegue hasta la carpeta e identifique el nombre de la aplicación de programa previo. El nombre de la aplicación de programa previo depende del valor de ProductId especificado al generar el diseño mínimo. Consulte la tabla siguiente para obtener ejemplos comunes.

|Valor de ProductId    |Nombre de la aplicación|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

La actualización se aplica a una instancia de Visual Studio en dos pasos. Empiece por actualizar el Instalador de Visual Studio. Después, actualice Visual Studio.

1. **Actualización del Instalador de Visual Studio** 

    Ejecute el comando siguiente; sustituya `vs_enterprise.exe` por el nombre de aplicación de programa previo correcto si es necesario. 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Actualización de la aplicación de Visual Studio**

    Para actualizar Visual Studio, debe especificar el valor installPath de la instancia de Visual Studio que quiera actualizar. Si hay varias instancias de Visual Studio instaladas, cada una debe actualizarse por separado. Se recomienda especificar la opción `–noWeb` con el comando de actualización para evitar la instalación de componentes que no formen parte del diseño mínimo. Esto le impide dejar Visual Studio en un estado inutilizable.

    Ejecute el siguiente comando; sustituya el parámetro de línea de comandos installPath correctamente. Asegúrese de usar también el nombre de aplicación de programa previo correcto.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalación de Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Definición de la configuración en un archivo de respuesta](automated-installation-with-response-file.md)
* [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing/)
