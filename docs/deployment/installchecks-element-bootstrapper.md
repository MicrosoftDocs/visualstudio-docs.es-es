---
title: "&lt;InstallChecks&gt; (Elemento, Arranque) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<InstallChecks> (elemento) [arranque]"
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# &lt;InstallChecks&gt; (Elemento, Arranque)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento `InstallChecks` permite iniciar varias pruebas en relación con el equipo local para asegurarse de que se han instalado todos los requisitos previos de una aplicación.  
  
## Sintaxis  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## AssemblyCheck  
 Este elemento es un elemento secundario opcional de `InstallChecks`.  En cada instancia de `AssemblyCheck`, el arranque garantizará que el ensamblado identificado por el elemento existe en la memoria caché global de ensamblados \(GAC\).  No contiene elementos y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Property`|Obligatorio.  El nombre de la propiedad que permite almacenar el resultado.  Se puede hacer referencia a esta propiedad desde una prueba debajo del elemento `InstallConditions`, que es un elemento secundario del elemento `Command`.  Para obtener más información, vea [\<Commands\> \(Elemento\)](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Obligatorio.  Nombre completo del ensamblado que se va a comprobar.|  
|`PublicKeyToken`|Obligatorio.  El formulario abreviado de la clave pública asociado con este ensamblado de nombre seguro.  Todos los ensamblados almacenados en la GAC deben tener un nombre, una versión y una clave pública.|  
|`Version`|Obligatorio.  Versión del ensamblado.<br /><br /> El número de versión tiene el formato \<*versión principal*\>.\<*versión secundaria*\>.\<*versión de compilación*\>.\<*versión de revisión*\>.|  
|`Language`|Opcional.  El lenguaje de un ensamblado traducido.  El valor predeterminado es `neutral`.|  
|`ProcessorArchitecture`|Opcional.  El procesador del equipo de destino de esta instalación.  El valor predeterminado es `msil`.|  
  
## ExternalCheck  
 Este elemento es un elemento secundario opcional de `InstallChecks`.  Para cada instancia de `ExternalCheck`, el arranque ejecutará el programa externo especificado en un proceso independiente y almacenará su código de salida en la propiedad indicada por `Property`.  `ExternalCheck` es útil para implementar las comprobaciones de la dependencia complejas o cuando la única manera de comprobar la existencia de un componente es creando instancias de él.  
  
 `ExternalCheck` no contiene elementos y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Property`|Obligatorio.  El nombre de la propiedad que permite almacenar el resultado.  Se puede hacer referencia a esta propiedad desde una prueba debajo del elemento `InstallConditions`, que es un elemento secundario del elemento `Command`.  Para obtener más información, vea [\<Commands\> \(Elemento\)](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Obligatorio.  El programa externo que se va a ejecutar.  El programa debe formar parte del paquete de distribución de instalación.|  
|`Arguments`|Opcional.  Proporciona los argumentos de la línea de comandos a la aplicación ejecutable nombrada por `PackageFile`.|  
  
## FileCheck  
 Este elemento es un elemento secundario opcional de `InstallChecks`.  Para cada instancia de `FileCheck`, el arranque determinará si el archivo con nombre existe, y devolverá el número de versión del archivo.  Si el archivo no tiene un número de versión, el arranque establecerá en 0 la propiedad especificada por `Property`..  Si el archivo no existe, `Property` no se establece en ningún valor.  
  
 `FileCheck` no contiene elementos y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Property`|Obligatorio.  El nombre de la propiedad que permite almacenar el resultado.  Se puede hacer referencia a esta propiedad desde una prueba debajo del elemento `InstallConditions`, que es un elemento secundario del elemento `Command`.  Para obtener más información, vea [\<Commands\> \(Elemento\)](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Obligatorio.  Nombre del archivo que se va a buscar.|  
|`SearchPath`|Obligatorio.  El disco o carpeta en la que buscar el archivo.  Debe ser una ruta de acceso relativa si se asigna `SpecialFolder`; en caso contrario, debe ser una ruta de acceso absoluta.|  
|`SpecialFolder`|Opcional.  Una carpeta que tiene importancia especial para Windows o para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  El valor predeterminado es interpretar `SearchPath` como una ruta de acceso absoluta.  Los valores válidos son los siguientes:<br /><br /> `AppDataFolder`.  La carpeta de datos de esta aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]; es específica para el usuario actual.<br /><br /> `CommonAppDataFolder`.  La carpeta de datos de la aplicación utilizada por todos los usuarios.<br /><br /> `CommonFilesFolder`.  La carpeta Archivos comunes del usuario actual.<br /><br /> `LocalDataAppFolder`.  La carpeta de datos para las aplicaciones no móviles.<br /><br /> `ProgramFilesFolder`.  La carpeta Archivos de programa estándar para las aplicaciones de 32 bits.<br /><br /> `StartUpFolder`.  La carpeta que contiene todas las aplicaciones iniciadas en el inicio del sistema.<br /><br /> `SystemFolder`.  La carpeta que contiene los archivos DLL del sistema de 32 bits.<br /><br /> `WindowsFolder`.  La carpeta que contiene la instalación del sistema de Windows.<br /><br /> `WindowsVolume`.  La unidad o partición que contiene la instalación del sistema de Windows.|  
|`SearchDepth`|Opcional.  La profundidad con que buscar el archivo con nombre en las subcarpetas.  La búsqueda se realiza primero en profundidad.  El valor predeterminado es 0, lo que restringe la búsqueda a la carpeta de nivel superior especificada por `SpecialFolder` y **SearchPath**.|  
  
## MsiProductCheck  
 Este elemento es un elemento secundario opcional de `InstallChecks`.  En cada instancia de `MsiProductCheck`, el arranque comprueba si la instalación de Microsoft Windows Installer especificada se ha ejecutado hasta completarse.  El valor de propiedad se establece en función del estado del producto instalado.  Un valor positivo indica que el producto está instalado, 0 ó \-1 indican que no está instalado.  \(Consulte la función del SDK de Windows Installer MsiQueryFeatureState para obtener más información\). .  Si Windows Installer no está instalado en el equipo, no se ha configurado `Property`.  
  
 `MsiProductCheck` no contiene elementos y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Property`|Obligatorio.  El nombre de la propiedad que permite almacenar el resultado.  Se puede hacer referencia a esta propiedad desde una prueba debajo del elemento `InstallConditions`, que es un elemento secundario del elemento `Command`.  Para obtener más información, vea [\<Commands\> \(Elemento\)](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Obligatorio.  El GUID del producto instalado.|  
|`Feature`|Opcional.  El GUID de una característica concreta de la aplicación instalada.|  
  
## RegistryCheck  
 Este elemento es un elemento secundario opcional de `InstallChecks`.  En cada instancia de `RegistryCheck`, el arranque comprueba si existe la clave del Registro especificada o si tiene el valor indicado.  
  
 `RegistryCheck` no contiene elementos y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Property`|Obligatorio.  El nombre de la propiedad que permite almacenar el resultado.  Se puede hacer referencia a esta propiedad desde una prueba debajo del elemento `InstallConditions`, que es un elemento secundario del elemento `Command`.  Para obtener más información, vea [\<Commands\> \(Elemento\)](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obligatorio.  Nombre de la clave del Registro.|  
|`Value`|Opcional.  Nombre del valor del Registro que se va a recuperar.  El valor predeterminado es devolver el texto del valor predeterminado.  `Value` debe ser String o DWORD.|  
  
## RegistryFileCheck  
 Este elemento es un elemento secundario opcional de `InstallChecks`.  Por cada instancia de `RegistryFileCheck`, el arranque recupera la versión del archivo especificado, intentando primero recuperar la ruta de acceso al archivo desde la clave del Registro especificada.  Esto resulta especialmente útil si desea buscar un archivo en un directorio especificado como un valor del Registro.  
  
 `RegistryFileCheck` no contiene elementos y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Property`|Obligatorio.  El nombre de la propiedad que permite almacenar el resultado.  Se puede hacer referencia a esta propiedad desde una prueba debajo del elemento `InstallConditions`, que es un elemento secundario del elemento `Command`.  Para obtener más información, vea [\<Commands\> \(Elemento\)](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obligatorio.  Nombre de la clave del Registro.  Su valor se interpreta como la ruta de acceso a un archivo, a menos que se establezca el atributo `File`.  Si esta clave no existe, no se establece `Property`.|  
|`Value`|Opcional.  Nombre del valor del Registro que se va a recuperar.  El valor predeterminado es devolver el texto del valor predeterminado.  `Value` debe ser una cadena.|  
|`FileName`|Opcional.  Nombre de un archivo .  Si se especifica, se supone que el valor obtenido de la clave del Registro es una ruta de acceso al directorio y dicho nombre se adjunta.  Si no se especifica, se supone que el valor devuelto del Registro es la ruta de acceso completa a un archivo.|  
|`SearchDepth`|Opcional.  La profundidad con que buscar el archivo con nombre en las subcarpetas.  La búsqueda se realiza primero en profundidad.  El valor predeterminado es 0, lo que restringe la búsqueda a la carpeta de nivel superior especificada por el valor de la clave del Registro.|  
  
## Comentarios  
 Los elementos bajo `InstallChecks` definen las comprobaciones que se ejecutarán, pero no las ejecutan.  Para ejecutar las comprobaciones, es necesario crear elementos `Command` bajo el elemento `Commands`.  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra el elemento `InstallChecks` tal y como se utiliza en el archivo de producto de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## InstallConditions  
 Cuando se evalúan `InstallChecks`, generan las propiedades.  Las condiciones `InstallConditions` utilizan a continuación las propiedades para determinar si un paquete debe instalarse, omitirse o producir un error.  En la tabla siguiente se muestran las condiciones `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Si cualquier condición `FailIf` se evalúa como true, se producirá un error en el paquete.  El resto de las condiciones no se evaluarán.|  
|`BypassIf`|Si alguna condición `BypassIf` se evalúa como true, se omitirá el paquete.  El resto de las condiciones no se evaluarán.|  
  
## Propiedades predefinidas  
 En la tabla siguiente se muestran los elementos `BypassIf` y `FailIf`.  
  
|Propiedad.|Notas|Valores posibles|  
|----------------|-----------|----------------------|  
|`Version9X`|Número de versión de un sistema operativo Windows 9X.|4.10 \= Windows 98|  
|`VersionNT`|Número de versión de un sistema operativo basado en Windows NT.|Major.Minor.ServicePack<br /><br /> 5.0 \= Windows 2000<br /><br /> 5.1.0 \= Windows XP<br /><br /> 5.1.2 \= Windows XP Professional SP2<br /><br /> 5.2.0 \= Windows Server 2003|  
|`VersionNT64`|Número de versión de un sistema operativo basado en Windows NT de 64 bits.|Igual que el mencionado previamente.|  
|`VersionMsi`|Número de versión del servicio de Windows Installer.|2.0 \= Windows Installer 2.0|  
|`AdminUser`|Especifica si un usuario tiene privilegios de administrador en un sistema operativo basado en Windows NT.|0 \= sin privilegios de administrador<br /><br /> 1 \= con privilegios de administrador|  
  
 Por ejemplo, para bloquear la instalación en un equipo en el que se ejecuta Windows 95, utilice código como el siguiente:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## Vea también  
 [\<Commands\> \(Elemento\)](../deployment/commands-element-bootstrapper.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)