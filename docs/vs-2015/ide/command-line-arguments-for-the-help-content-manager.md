---
title: Argumentos de línea de comandos para Help Content Manager | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae1643b4a01c9bcab3878ec82b1808444cdc7712
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54778635"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Argumentos de línea de comandos para Help Content Manager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se puede especificar cómo implementar y administrar el contenido de la Ayuda local mediante los argumentos de la línea de comandos de Help Content Manager (HlpCtntmgr.exe). Los scripts de esta herramienta de la línea de comandos se deben ejecutar con permisos de administrador y no se pueden ejecutar como servicio. Con esta herramienta se pueden realizar las siguientes tareas:  
  
- Agregar o actualizar el contenido de la Ayuda local desde un disco o desde la nube.  
  
- Quitar el contenido de Ayuda local.  
  
- Mover el almacén de contenido de Ayuda local.  
  
- Agregar, actualizar, quitar o mover el contenido de Ayuda local de forma silenciosa.  
  
  Sintaxis:  
  
```  
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint  
```  
  
 Por ejemplo:  
  
```  
hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha  
```  
  
## <a name="switches-and-arguments"></a>Modificadores y argumentos  
 En la tabla siguiente se definen los modificadores y los argumentos que puede utilizar para la herramienta de la línea de comandos de Help Content Manager:  
  
|Modificador|¿Obligatorio?|Argumentos|  
|------------|---------------|---------------|  
|/operation|Sí|-   **Instalar**: agrega los libros del origen de instalación especificado al almacén de contenido local.<br />     Este modificador requiere el argumento /booklist, el argumento /sourceURI o ambos. Si no se especifica el argumento /sourceURI, el URI de Visual Studio predeterminado se utiliza como origen de la instalación. Si no se especifica el argumento /booklist, se instalarán todos los libros de /sourceUri.<br />-   **Desinstalar**: quita los libros que especifique del almacén de contenido local.<br />     Este modificador requiere el argumento /booklist o el argumento /sourceURI.  Si se especifica el argumento /sourceURI, se quitan todos los libros y se omite el argumento /booklist.<br />-   **Mover**: mueve el almacén local a la ruta de acceso especificada. La ruta de acceso predeterminada del almacén local se establece mediante la configuración de Ayuda en %PROGRAMDATA%<br />     Este modificador requiere los argumentos /locationPath y /catalogName. Los mensajes de error se graban en el registro de eventos si especifica una ruta de acceso no válida o si la unidad no contiene suficiente espacio disponible para albergar el contenido.<br />-   **Actualizar**: actualiza los temas que han cambiado desde que se instalaron o actualizaron recientemente.<br />     Este modificador requiere el argumento /sourceURI.|  
|/catalogName|Sí|Especifica el nombre del catálogo de contenido.|  
|/locale|No|Especifica la configuración regional del producto que se utiliza para ver y administrar el contenido de la instancia actual del Visor de Ayuda. Por ejemplo, se especifica `EN-US` para inglés (Estados Unidos).<br /><br /> Si no se especifica una configuración regional, se utiliza la del sistema operativo. Si esa configuración regional no se puede determinar, se utiliza `EN-US`.<br /><br /> Si se especifica una configuración regional no válida, se graba un mensaje de error en el registro de eventos.|  
|/e|No|Eleva Help Content Manager a los privilegios administrativos si el usuario actual tiene credenciales administrativas.|  
|/sourceURI|No|Especifica la dirección URL en la que se instala el contenido (API de servicio) o la ruta de acceso al archivo de instalación de contenido (.msha). La dirección URL puede apuntar al grupo de productos (nodo de nivel superior) o a los libros de productos (nodo en el nivel de hoja) en un punto de conexión de estilo Visual Studio 2010. No es necesario incluir una barra diagonal (/) al final de la dirección URL. Si incluye una barra diagonal final, se controlará adecuadamente.<br /><br /> Se graba un mensaje de error en el registro de eventos si especifica un archivo que no se encuentra, que no es válido o no es accesible, o bien si una conexión a Internet no está disponible o se interrumpe mientras se está administrando el contenido.|  
|/vendor|No|Especifica el proveedor para el contenido del producto que se quitará (por ejemplo, `Microsoft`). El argumento predeterminado para este modificador es Microsoft.|  
|/productName|No|Especifica el nombre de producto para los libros que se van a quitar. El nombre de producto se identifica en los archivos helpcontentsetup.msha o books.html que se incluye con el contenido. Puede quitar los libros de un único producto al mismo tiempo. Para quitar libros de varios productos, debe realizar varias instalaciones.|  
|/booklist|No|Especifica los nombres de los libros que se administrarán, separados por espacios. Los valores deben coincidir con los nombres del libro tal como se indica en el disco de instalación.<br /><br /> Si no especifica este argumento, se instalarán todos los libros recomendados para el producto especificado en /sourceURI si el origen de instalación está en el formato de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].<br /><br /> Si el nombre de un libro contiene uno o varios espacios, inclúyalo entre comillas dobles (") para delimitar la lista correctamente.<br /><br /> Los mensajes de error se registrarán si se especifica un modificador /sourceURI que no es válido o es inaccesible.|  
|/skuId|No|Especifica la referencia de almacén (SKU) del producto del origen de instalación y filtra los libros que el modificador /SourceURI identifica.|  
|/membership|No|-   **Mínima**: instala un conjunto mínimo de contenido de Ayuda basado en el SKU especificado mediante el modificador /skuId. La asignación entre SKU y el conjunto de contenido se expone en la API de servicio.<br />-   **Recomendada**: instala un conjunto de libros recomendados para el SKU especificado con el argumento /skuId. El origen de instalación es la API de servicio o .MSHA.<br />-   **Completa**: instala el conjunto completo de libros para el SKU especificado con el argumento /skuId. El origen de instalación es la API de servicio o .MSHA.|  
|/locationpath|No|Especifica la carpeta predeterminada para el contenido de Ayuda local. Debe utilizar este modificador para instalar o mover solo el contenido. Si especifica este modificador, también debe especificar el modificador /silent.|  
|/silent|No|Instala o quita contenido de Ayuda sin preguntar al usuario ni mostrar ninguna interfaz de usuario, incluido el icono en el área de notificación de estado. La salida se registra en un archivo en el directorio %Temp%. **Importante:** Para instalar contenido de forma silenciosa, debe usar los archivos .cab firmados digitalmente, no los archivos .mshc.|  
|/launchingApp|No|Define la aplicación y el contexto de catálogo cuando el Visor de Ayuda se inicia sin la aplicación primaria. Los argumentos para este modificador son *CompanyName*, *ProductName* y *VersionNumber* (por ejemplo, `/launchingApp Microsoft,VisualStudio,11.0`).<br /><br /> Esto es necesario para instalar contenido con el parámetro /silent.|  
|/wait *Segundos*|No|Pausa las operaciones de instalación, desinstalación y actualización. Si una operación ya está en curso para el catálogo, el proceso esperará hasta el número especificado de segundos para continuar. Use 0 para esperar indefinidamente.|  
|/?|No|Hace una lista de los modificadores y sus descripciones para la herramienta de la línea de comandos de Help Content Manager.|  
  
### <a name="exit-codes"></a>Códigos de salida  
 Cuando la herramienta de la línea de comandos de Help Content Manager se ejecuta en modo silencioso, devuelve los siguientes códigos de salida:  
  
```  
Success = 0,  
  
FailureToElevate = 100  
InvalidCmdArgs = 101,  
FailOnFetchingOnlineContent = 110,  
FailOnFetchingContentFromDisk = 120,  
FailOnFetchingInstalledBooks = 130,  
NoBooksToUninstall = 200,  
NoBooksToInstall = 300,  
FailOnUninstall = 400,  
FailOnInstall = 500,  
FailOnMove = 600,  
FailOnUpdate = 700,  
FailOnRefresh = 800,  
Cancelled = 900,  
Others = 999,  
ContentManagementDisabled = 1200,  
OnlineHelpPreferenceDisabled = 1201  
UpdateAlreadyRunning = 1300 – (Signals that the update didn't run because another was in progress.)  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Guía del administrador del Visor de Ayuda](../ide/help-viewer-administrator-guide.md)   
 [Invalidaciones de Help Content Manager](../ide/help-content-manager-overrides.md)
