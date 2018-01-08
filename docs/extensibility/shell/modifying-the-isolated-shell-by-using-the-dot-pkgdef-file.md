---
title: Modificar el Shell aislado mediante el. Pkgdef del archivo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f250d81ec35a2d9de074f54dded1f7ef0d76ef09
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>Modificar el Shell aislado mediante el. Pkgdef del archivo
El archivo .pkgdef admite la configuración que puede usar para personalizar una aplicación de shell aislado. Especifica valores que se crean cuando se instala una aplicación en un equipo y que se hace referencia mediante el shell de Visual Studio cuando se inicia la aplicación. La configuración se organiza en el archivo en función de las claves del registro es aplicable.  
  
> [!WARNING]
>  Tenga en cuenta que no se analizan archivos .pkgdef que no se declaran en el archivo .vsixmanifest del VSPackage cuando se inicia Visual Studio.  
  
 El archivo .pkgdef contiene secciones que son cada una identificada por una clave, ya sea `[$RootKey$]` o `[$RootKey$\` *subclave*`]`, donde $RootKey$ es la clave raíz para la aplicación.  
  
 Cada sección contiene los pares de nombre/valor que tienen el siguiente formato: `"` *nombreDeValor*`"=`*valor*.  
  
 Los valores son una cadena que se encierra entre comillas o un entero de 32 bits que se representa como un valor dword. Valores tienen las siguientes restricciones:  
  
-   Todos los valores de dword están en formato hexadecimal, por ejemplo `dword:00000001`.  
  
     Para valores booleanos, 1 representa true y 0 representa false.  
  
-   Todas las cadenas GUID están en formato de registro, por ejemplo, `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   Todos los identificadores de recursos localizables tienen el formato "@*resourceID*" o "#*resourceID*", donde *resourceID* es el identificador de recursos en el paquete de interfaz de usuario de la aplicación, Por ejemplo, `"@102"`. El paquete de interfaz de usuario de aplicación es el paquete que se hace referencia en la configuración de AppLocalizationPackage.  
  
 Por ejemplo,  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 Puede agregar comentarios en el archivo .pkgdef. Una sola línea de comentario tiene dos barras diagonales como los dos primeros caracteres.  
  
 Para obtener una lista de las cadenas de sustitución, consulte [utilizan las cadenas de sustitución de. Pkgdef del y. Archivos de Pkgundef](substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 Las siguientes secciones describen determinados valores del registro que afectan al comportamiento del shell de Visual Studio en modo aislado. También puede definir valores de registro adicionales para la aplicación en este archivo.  
  
> [!NOTE]
>  Si no se proporciona una configuración en el archivo .pkgdef, a continuación, se realiza ninguna entrada correspondiente en el registro.  
  
## <a name="settings"></a>Configuración  
 La tabla siguiente describen los valores definidos en [$RootKey$].  
  
|nombre|Tipo|Valor|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True si se pueden cargar complementos; en caso contrario, false.<br /><br /> El valor predeterminado es true.|  
|AllowsDroppedFilesOnMainWindow|dword|True si la ventana principal puede aceptar archivos colocados; en caso contrario, false. Archivos que se coloquen en la ventana principal se abren mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> método. Esto es equivalente a la apertura de un documento mediante el uso de la **abiertos** comando el **archivo** menú de la aplicación.<br /><br /> El valor predeterminado es true.|  
|AppIcon|cadena|La ruta de acceso completa del icono del programa. Este icono aparece en la barra de título a la izquierda del nombre de aplicación.<br /><br /> El valor predeterminado es "$RootFolder$\\*nombresolución*.ico", donde *solutionName* es el nombre del archivo de solución de aplicación.|  
|AppLocalizationPackage|cadena|El GUID del VSPackage que contiene el ensamblado satélite de interfaz de usuario para la aplicación. Este paquete de VS incluye una versión compilada del archivo .vsct y puede incluir otras cadenas localizadas. Conjuntos de características y los grupos de comandos de menú se pueden habilitar o deshabilitar cambiando la configuración en el archivo .vsct de proyecto de interfaz de usuario.<br /><br /> El valor predeterminado es "{*vsUiPackageGuid*}", donde *vsUiPackageGuid* es el GUID asignado al paquete de interfaz de usuario de aplicación.|  
|AppName|cadena|El nombre de la aplicación. El nombre aparece en la barra de título de la ventana de la aplicación.<br /><br /> El valor predeterminado es el nombre del archivo de solución de aplicación.|  
|CommandLineLogo|cadena|El texto de titular cuando la aplicación se ejecuta en una ventana de consola. Esta configuración sólo afecta a aplicaciones que admiten operaciones de compilación de línea de comandos.<br /><br /> El valor predeterminado es "*companyName**nombresolución* versión 1.0.", donde *companyName* es el nombre de la compañía que se proporcionó cuando se instaló Windows y *solutionName* es el nombre del archivo de solución de aplicación.|  
|DefaultDebugEngine|cadena|El GUID del valor predeterminado de depuración motor que se usará para la aplicación.<br /><br /> Nota: Un GUID vacío (todo ceros) indica que la aplicación no especifica un motor de depuración predeterminado. Esto permite al depurador seleccionar el motor de depuración que deseas usar.<br /><br /> El valor predeterminado es "{00000000-0000-0000-0000-000000000000}".|  
|DefaultHomePage|cadena|Dirección URL de página principal predeterminada de la ventana del explorador Web interna.<br /><br /> Si el **página principal** opción está disponible en la aplicación, a continuación, esta configuración también afecta al estado predeterminado de la opción. Para obtener más información, consulte [cuadro de diálogo de explorador Web, entorno, opciones](../../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> El valor predeterminado es la dirección URL de la compañía que se proporcionó cuando se instaló Windows.|  
|DefaultProjectsLocation|cadena|La ruta de acceso completa de la carpeta de proyectos predeterminada. Por ejemplo,<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> Si el **ubicación de proyectos de Visual Studio** opción está disponible en la aplicación, a continuación, esta configuración también afecta al estado predeterminado de la opción. Para obtener más información, consulte [NIB: General, proyectos y soluciones, cuadro de diálogo Opciones](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> El valor predeterminado es "$MyDocuments$\\*nombresolución*", donde *solutionName* es el nombre del archivo de solución de aplicación.|  
|DefaultSearchPage|cadena|La búsqueda página dirección URL predeterminada para la ventana del explorador Web interna.<br /><br /> Si el **página de búsqueda** opción está disponible en la aplicación, a continuación, esta configuración también afecta al estado predeterminado de la opción. Para obtener más información, consulte [cuadro de diálogo de explorador Web, entorno, opciones](../../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> El valor predeterminado es "http://search.live.com".|  
|DefaultUserFilesFolderRoot|cadena|El nombre de la carpeta de usuario, en relación con el usuario actual de la carpeta Mis documentos del.<br /><br /> El valor predeterminado es el nombre del archivo de solución de aplicación.|  
|DisableOutputWindow|dword|Indica si el shell aislado debe tratar la ventana de salida como deshabilitados.<br /><br /> Si este valor se establece en true, Visual Studio no muestra el resultado de administrador de compilación de soluciones en el **salida** ventana y oculta el **Mostrar ventana de salida cuando empiece la compilación** casilla de verificación en la  **Proyectos y soluciones** categoría en la **opciones** cuadro de diálogo.<br /><br /> El valor predeterminado es false.|  
|HideMiscellaneousFilesByDefault|dword|True para ocultar el **archivos varios** carpeta de forma predeterminada en **el Explorador de soluciones**; de lo contrario, false.<br /><br /> Si el **mostrar archivos varios en el Explorador de soluciones** opción está disponible en la aplicación, a continuación, esta configuración también afecta al estado predeterminado de la opción. Para obtener más información, consulte [documentos, entorno, cuadro de diálogo de opciones](../../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> El valor predeterminado es false.|  
|HideSolutionConcept|dword|Es True para crear proyectos de todos los proyectos como independientes y ocultar la solución y los comandos relacionados con la solución para proyectos independientes de forma predeterminada; en caso contrario, false.<br /><br /> Si el **Mostrar solución siempre** opción está disponible en la aplicación, a continuación, esta configuración también afecta al estado predeterminado de la opción. Para obtener más información, consulte [NIB: General, proyectos y soluciones, cuadro de diálogo Opciones](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> El valor predeterminado es false.|  
|NewProjDlgInstalledTemplatesHdr|cadena|El nombre para el encabezado de plantillas de Visual Studio instalados en el **plantillas** lista en la **nuevo proyecto** cuadro de diálogo. Se trata de una cadena o un identificador de recurso localizable que se carga desde el paquete de interfaz de usuario de la aplicación.<br /><br /> El valor predeterminado es "*nombresolución* plantillas instaladas", donde *solutionName* es el nombre del archivo de solución de aplicación.|  
|NewProjDlgSlnTreeNodeTitle|cadena|El nombre de la **soluciones de Visual Studio** nodo en el **tipos de proyecto** de árbol en el **nuevo proyecto** cuadro de diálogo. Se trata de una cadena o un identificador de recurso localizable que se carga desde el paquete de interfaz de usuario de la aplicación.<br /><br /> El valor predeterminado es "*nombresolución* plantillas instaladas", donde *solutionName* es el nombre del archivo de solución de aplicación.|  
|SolutionFileCreatorIdentifier|cadena|El identificador de la aplicación, que aparece como la segunda línea en los archivos de solución generadas por la aplicación. Esta línea indica que la aplicación que creó el archivo. Por convención, este valor incluye el nombre de la aplicación y el número de versión de la aplicación. Por ejemplo,<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> El programa VSLauncher.exe, que es el programa predeterminado para abrir un archivo de solución de Visual Studio, usa esta segunda línea para determinar la versión de Visual Studio en el que se va a abrir el archivo de solución. La aplicación requiere su propio selector para administrar sus archivos de solución asociado. El iniciador también puede usar esta segunda línea en el archivo de solución para determinar en qué versión de la aplicación para abrir la solución.<br /><br /> Nota: El programa de Visual VSLauncher.exe Studio no controla .sln (archivos) que se crearon mediante una aplicación de shell aislado.<br /><br /> El valor predeterminado es "*nombresolución* archivo de solución, versión de formato de 10,00", donde *solutionName* es el nombre del archivo de solución de aplicación.|  
|SolutionFileExt|cadena|La extensión de nombre de archivo de solución para la aplicación. Se recomienda que elija una extensión de nombre de archivo único (not.sln).<br /><br /> El valor predeterminado es "*nombresolución*_sln", donde *solutionName* es el nombre del archivo de solución de aplicación.|  
|SplashScreenBitmap|cadena|La ruta de acceso completa del archivo de mapa de bits de la pantalla de presentación de la aplicación.<br /><br /> El valor predeterminado es "$RootFolder$\Splash.bmp".|  
|ThisVersionDTECLSID|cadena|El identificador de clase (CLSID) del objeto de automatización de la aplicación.<br /><br /> El objeto de automatización de la aplicación es el objeto de nivel superior para la aplicación en el modelo de automatización de Visual Studio shell e implementa el <xref:EnvDTE._DTE?displayProperty=fullName> interfaz.<br /><br /> Si el objeto de automatización de la aplicación se ha registrado correctamente en la clave del Registro HKEY_CLASSES_ROOT\CLSID, puede usar el [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) función para crear directamente una instancia de la aplicación.<br /><br /> El shell de Visual Studio utiliza este CLSID para registrar el objeto de automatización de la aplicación en la tabla de objetos en ejecución (ROT) mediante la marca ACTIVEOBJECT_WEAK. Esto le permite usar la [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)función para recuperar un puntero a una instancia en ejecución de la aplicación. Además, si define un ProgID para el objeto de automatización de la aplicación, a continuación, el shell de Visual Studio también registra cada instancia de la aplicación en la tabla ROT utilizando un moniker del elemento del formulario *progID*:*processID* , donde *progID* es el ProgID del objeto de automatización de la aplicación, y *processID* es el identificador de proceso para esa instancia de la aplicación. Por ejemplo, si crea un moniker como sigue:<br /><br /> `CreateItemMoniker(L"!",`  *instanceString*`, &instanceMoniker)`<br /><br /> donde `instanceString` es el *progID*:*processID* cadena. podría usar `instanceMoniker` con la función GetObject ROT para obtener la instancia.<br /><br /> Si se omite la configuración de ThisVersionDTECLSID, la aplicación no se expone a través del modelo de objetos componentes (COM). En este caso, no se puede crear una instancia de la aplicación mediante una llamada a la [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) función y no se puede registrar en la tabla ROT.<br /><br /> Cada versión de un paquete VSPackage debe tener un CLSID diferente.<br /><br /> El valor predeterminado es el GUID que genera Visual Studio para el objeto de automatización de la aplicación.|  
|ThisVersionSolutionCLSID|cadena|Identificador CLSID del objeto de solución para la aplicación.<br /><br /> El objeto de automatización de la solución contiene información sobre la solución abierta actual en una instancia de la aplicación y la implementa el <xref:EnvDTE._Solution?displayProperty=fullName> interfaz.<br /><br /> Si el objeto de automatización de la solución se ha registrado correctamente en la clave del Registro HKEY_CLASSES_ROOT\CLSID, puede usar el [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) función para crear directamente un objeto de la solución para la aplicación.<br /><br /> El shell de Visual Studio utiliza este CLSID para registrar el objeto de automatización de la solución en la tabla ROT mediante la marca ACTIVEOBJECT_WEAK.<br /><br /> Si se omite esta configuración, a continuación, la clase de la solución no está registrada con el modelo de objetos componentes (COM) y no se puede crear un objeto de la solución mediante una llamada a la [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) función y no se puede registrar en la tabla ROT.<br /><br /> El valor predeterminado es un GUID que genera Visual Studio para el objeto de solución de la aplicación.|  
|UserFilesSubFolderName|cadena|El nombre de la subcarpeta en la carpeta de Mis documentos del usuario en el que la aplicación crea subcarpetas y archivos de usuario.<br /><br /> El valor predeterminado es el nombre del archivo de solución de aplicación.|  
|UserOptsFileExt|cadena|La extensión para los archivos de opciones de usuario de solución para la aplicación.<br /><br /> El valor predeterminado es el nombre del archivo de solución de aplicación.|  
  
## <a name="binding-path-settings"></a>Configuración de la ruta de acceso de enlace  
 El [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] clave contiene la lista de directorios que el shell busca ensamblados. Estos directorios se agregan a la lista de directorios que el shell busca ensamblados privados de la aplicación.  
  
 De forma predeterminada, no hay entradas de ruta de acceso de enlace se agregan al archivo .pkgdef. Sin embargo, los siguientes subdirectorios del directorio de instalación de Visual Studio se agregan automáticamente a la lista de rutas de acceso de enlace de la aplicación en el registro.  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 Para agregar un directorio a la ruta de acceso de enlace, agregue una entrada de la forma "*directoryName*"="", donde *directoryName* es una ruta absoluta. Por ejemplo,  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>Configuración de perfil  
 En la tabla siguiente se describe los valores que se definen para cada paquete asociado bajo [$RootKey$ \Profile].  
  
|nombre|Tipo|Valor|  
|----------|----------|-----------|  
|AutoSaveFile|cadena|El directorio en el que la aplicación almacena los archivos de guardado automático.<br /><br /> El valor predeterminado es "$RootFolder$\Profiles\CurrentSettings.vssettings".|  
  
## <a name="package-satellite-dll-settings"></a>Configuración de la DLL satélite paquete  
 En la tabla siguiente se describe los valores que se definen en [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] de la DLL de cada paquete asociado, satélite donde *vsPackageGuid* es el GUID del paquete asociado.  
  
|nombre|Tipo|Valor|  
|----------|----------|-----------|  
|Nombre dll|cadena|El nombre de archivo del archivo DLL.<br /><br /> El valor predeterminado es "*nombresolución*ui.dll", donde *solutionName* es el nombre del archivo de solución de aplicación.|  
|Ruta de acceso|cadena|El directorio que contiene el archivo DLL satélite.<br /><br /> El valor predeterminado es "$PackageFolder$".|  
  
## <a name="package-menu-item-settings"></a>Configuración del elemento de menú de paquete  
 La clave del registro [$RootKey$ \Menus] define los archivos de recursos de interfaz de usuario de la aplicación.  
  
 Valores de elemento de menú tienen el formato "{*vsUiPackageGuid*}"=", *resourceId*, *versionNumber*", donde *vsUiPackageGuid* es el GUID del el paquete de interfaz de usuario de la aplicación, *resourceId* es el identificador de recurso del recurso CTMENU que contiene los elementos de interfaz de usuario, y *versionNumber* es un número de versión virtual para el CTMENU recurso. Para obtener más información, consulte [registrar controladores de comandos del ensamblado de interoperabilidad](../internals/registering-interop-assembly-command-handlers.md).  
  
 De forma predeterminada, se crea una entrada de elemento de menú en el archivo .pkgdef para el paquete de interfaz de usuario de la aplicación.  
  
 Para cada paquete que proporciona elementos de menú y que se distribuye como parte de la aplicación, agregue una entrada de elemento de menú para el paquete.  
  
## <a name="see-also"></a>Vea también  
 [Personalizar el Shell aislado](customizing-the-isolated-shell.md)   
 [. Archivos de Pkgundef](modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)