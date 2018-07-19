---
title: '&lt;InstallChecks&gt; (elemento, arranque) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7dc1d480f10bad02547d30d0dfb3bf815b47cd64
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081288"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; (elemento, arranque)
El `InstallChecks` elemento admite el inicio de una variedad de pruebas en el equipo local para asegurarse de que se han instalado todos los requisitos previos para una aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
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
  
## <a name="assemblycheck"></a>AssemblyCheck  
 Este es un elemento secundario opcional de `InstallChecks`. Para cada instancia de `AssemblyCheck`, el programa previo se asegurará de que el ensamblado identificado por el elemento existe en la caché de ensamblados global (GAC). No contiene ningún elemento y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Property`|Requerido. El nombre de la propiedad para almacenar el resultado. Esta propiedad se puede hacer referencia a partir de una prueba debajo el `InstallConditions` elemento, que es un elemento secundario de la `Command` elemento. Para obtener más información, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Requerido. El nombre completo del ensamblado que se va a comprobar.|  
|`PublicKeyToken`|Requerido. La forma abreviada de la clave pública asociado a este ensamblado con nombre seguro. Todos los ensamblados almacenados en la GAC deben tener un nombre, una versión y una clave pública.|  
|`Version`|Requerido. Versión del ensamblado.<br /><br /> El número de versión tiene el formato \< *versión principal*>.\< *podverze*>.\< *versión de compilación*>.\< *versión de revisión*>.|  
|`Language`|Opcional. El idioma de un ensamblado localizado. El valor predeterminado es `neutral`.|  
|`ProcessorArchitecture`|Opcional. El procesador del equipo de destino con esta instalación. El valor predeterminado es `msil`.|  
  
## <a name="externalcheck"></a>ExternalCheck  
 Este es un elemento secundario opcional de `InstallChecks`. Para cada instancia de `ExternalCheck`, el programa previo ejecutará el programa externo con nombre en un proceso independiente y almacenar su código de salida en la propiedad indicada por `Property`. `ExternalCheck` es útil para implementar las comprobaciones de dependencias complejas, o si es la única manera de comprobar la existencia de un componente crear instancias de ella.  
  
 `ExternalCheck` no contiene ningún elemento y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Property`|Requerido. El nombre de la propiedad para almacenar el resultado. Esta propiedad se puede hacer referencia a partir de una prueba debajo el `InstallConditions` elemento, que es un elemento secundario de la `Command` elemento. Para obtener más información, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Requerido. Ejecutar el programa externo. El programa debe formar parte de la distribución del paquete de instalación.|  
|`Arguments`|Opcional. Proporciona argumentos de línea de comandos al archivo ejecutable denominado `PackageFile`.|  
  
## <a name="filecheck"></a>FileCheck  
 Este es un elemento secundario opcional de `InstallChecks`. Para cada instancia de `FileCheck`, el programa previo determinará si el archivo con nombre existe y devolver el número de versión del archivo. Si el archivo no tiene un número de versión, el programa previo establece la propiedad denominada por `Property` en 0. Si el archivo no existe, `Property` no está establecido en cualquier valor.  
  
 `FileCheck` no contiene ningún elemento y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Property`|Requerido. El nombre de la propiedad para almacenar el resultado. Esta propiedad se puede hacer referencia a partir de una prueba debajo el `InstallConditions` elemento, que es un elemento secundario de la `Command` elemento. Para obtener más información, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Requerido. El nombre del archivo que se va a buscar.|  
|`SearchPath`|Requerido. El disco o la carpeta en la que se va a buscar el archivo. Debe ser una ruta de acceso relativa si `SpecialFolder` está asignado; en caso contrario, debe ser una ruta de acceso absoluta.|  
|`SpecialFolder`|Opcional. Una carpeta que tenga un significado especial para Windows o a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. El valor predeterminado es interpretar `SearchPath` como una ruta de acceso absoluta. Los valores válidos son los siguientes:<br /><br /> `AppDataFolder`. La carpeta de datos de aplicación para este [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la aplicación; específicos del usuario actual.<br /><br /> `CommonAppDataFolder`. La carpeta de datos de aplicación utilizada por todos los usuarios.<br /><br /> `CommonFilesFolder`. La carpeta archivos comunes para el usuario actual.<br /><br /> `LocalDataAppFolder`. La carpeta de datos para las aplicaciones que no son móviles.<br /><br /> `ProgramFilesFolder`. La carpeta de archivos de programa estándar para las aplicaciones de 32 bits.<br /><br /> `StartUpFolder`. La carpeta que contiene todas las aplicaciones iniciadas en el inicio del sistema.<br /><br /> `SystemFolder`. La carpeta que contiene los archivos DLL de sistema de 32 bits.<br /><br /> `WindowsFolder`. La carpeta que contiene la instalación del sistema de Windows.<br /><br /> `WindowsVolume`. La unidad o partición que contiene la instalación del sistema de Windows.|  
|`SearchDepth`|Opcional. La profundidad en el que se va a buscar en subcarpetas para el archivo con nombre. La búsqueda es la prioridad de profundidad. El valor predeterminado es 0, lo que limita la búsqueda a la carpeta de nivel superior especificada por `SpecialFolder` y **SearchPath**.|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 Este es un elemento secundario opcional de `InstallChecks`. Para cada instancia de `MsiProductCheck`, el programa previo se comprueba para ver si ha ejecutado la instalación de Microsoft Windows Installer especificada hasta que se complete. El valor de propiedad se establece según el estado del producto instalado. Un valor positivo indica que el producto está instalado, 0 o -1 indica que no está instalado. (Vea la función de SDK de Windows Installer MsiQueryFeatureState para obtener más información). . Si Windows Installer no está instalado en el equipo, `Property` no está establecida.  
  
 `MsiProductCheck` no contiene ningún elemento y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Property`|Requerido. El nombre de la propiedad para almacenar el resultado. Esta propiedad se puede hacer referencia a partir de una prueba debajo el `InstallConditions` elemento, que es un elemento secundario de la `Command` elemento. Para obtener más información, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Requerido. El GUID para el producto instalado.|  
|`Feature`|Opcional. El GUID de una característica específica de la aplicación instalada.|  
  
## <a name="registrycheck"></a>RegistryCheck  
 Este es un elemento secundario opcional de `InstallChecks`. Para cada instancia de `RegistryCheck`, el programa previo comprueba si existe la clave del registro especificada, o si tiene el valor indicado.  
  
 `RegistryCheck` no contiene ningún elemento y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Property`|Requerido. El nombre de la propiedad para almacenar el resultado. Esta propiedad se puede hacer referencia a partir de una prueba debajo el `InstallConditions` elemento, que es un elemento secundario de la `Command` elemento. Para obtener más información, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Requerido. Nombre de la clave del Registro.|  
|`Value`|Opcional. El nombre del valor del registro para recuperar. El valor predeterminado es devolver el texto del valor predeterminado. `Value` debe ser una cadena o un valor DWORD.|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 Este es un elemento secundario opcional de `InstallChecks`. Para cada instancia de `RegistryFileCheck`, el programa previo recupera la versión del archivo especificado, en primer lugar intenta recuperar la ruta de acceso al archivo de la clave del registro especificada. Esto es especialmente útil si desea buscar un archivo en un directorio especificado como un valor en el registro.  
  
 `RegistryFileCheck` no contiene ningún elemento y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Property`|Requerido. El nombre de la propiedad para almacenar el resultado. Esta propiedad se puede hacer referencia a partir de una prueba debajo el `InstallConditions` elemento, que es un elemento secundario de la `Command` elemento. Para obtener más información, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Requerido. Nombre de la clave del Registro. Su valor se interpreta como la ruta de acceso a un archivo, a menos que el `File` está establecido. Si esta clave no existe, `Property` no está establecida.|  
|`Value`|Opcional. El nombre del valor del registro para recuperar. El valor predeterminado es devolver el texto del valor predeterminado. `Value` debe ser una cadena.|  
|`FileName`|Opcional. El nombre de un archivo. Si se especifica, se supone que el valor obtenido de la clave del registro una ruta de acceso de directorio y este nombre se anexa a él. Si no se especifica, el valor devuelto desde el registro se supone que la ruta de acceso completa a un archivo.|  
|`SearchDepth`|Opcional. La profundidad en el que se va a buscar en subcarpetas para el archivo con nombre. La búsqueda es la prioridad de profundidad. El valor predeterminado es 0, lo que restringe la búsqueda a la carpeta de nivel superior especificada por el valor de la clave del registro.|  
  
## <a name="remarks"></a>Comentarios  
 Mientras que los elementos subyacentes `InstallChecks` definir las pruebas se ejecuten, no se ejecutan. Para ejecutar las pruebas, se debe crear `Command` elementos bajo la `Commands` elemento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el `InstallChecks` elemento tal y como se usa en el archivo del producto para el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```xml  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 Cuando `InstallChecks` son evalúa, generan las propiedades. A continuación, utiliza las propiedades `InstallConditions` para determinar si debe instalar, omitir o producirá un error en un paquete. La siguiente tabla enumera el `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Si cualquier `FailIf` condición se evalúa como true, se producirá un error en el paquete. No se evaluará el resto de las condiciones.|  
|`BypassIf`|Si cualquier `BypassIf` condición se evalúa como true, el paquete se omitirán. No se evaluará el resto de las condiciones.|  
  
## <a name="predefined-properties"></a>Propiedades predefinidas  
 La siguiente tabla se enumeran los `BypassIf` y `FailIf` elementos:  
  
|Property|Notas|Valores posibles|  
|--------------|-----------|---------------------|  
|`Version9X`|Número de versión del sistema operativo Windows 9 X.|4.10 = Windows 98|  
|`VersionNT`|Número de versión de un sistema operativo basado en Windows NT.|Principal.secundaria.servicepack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Profesional SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|Número de versión de un sistema operativo basado en Windows NT de 64 bits.|Igual que se ha mencionado anteriormente.|  
|`VersionMsi`|Número de versión del servicio Windows Installer.|2.0 = Windows Installer 2.0|  
|`AdminUser`|Especifica si un usuario tiene privilegios de administrador en un sistema operativo basado en Windows NT.|0 no = privilegios de administrador<br /><br /> 1 = privilegios de administrador|  
  
 Por ejemplo, para bloquear la instalación en un equipo que ejecuta Windows 95, utilice código como el siguiente:  
  
```xml  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>Vea también  
 [\<Comandos > elemento](../deployment/commands-element-bootstrapper.md)   
 [Referencia de esquema de paquete y del producto](../deployment/product-and-package-schema-reference.md)