---
title: '&lt;&gt;Elemento InstallChecks (arranque) | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7ba4da072a586bdc09993b77200a769be3940ab
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536310"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;&gt;Elemento InstallChecks (arranque)
El `InstallChecks` elemento permite iniciar una serie de pruebas en el equipo local para asegurarse de que se han instalado todos los requisitos previos adecuados para una aplicación.

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
 Este elemento es un elemento secundario opcional de `InstallChecks` . Para cada instancia de `AssemblyCheck` , el programa previo se asegurará de que el ensamblado identificado por el elemento existe en la caché de ensamblados global (GAC). No contiene ningún elemento y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`Property`|Obligatorio. Nombre de la propiedad en la que se va a almacenar el resultado. Se puede hacer referencia a esta propiedad desde una prueba debajo del `InstallConditions` elemento, que es un elemento secundario del `Command` elemento. Para obtener más información, consulte [Elemento \<Commands>](../deployment/commands-element-bootstrapper.md).|
|`Name`|Obligatorio. Nombre completo del ensamblado que se va a comprobar.|
|`PublicKeyToken`|Obligatorio. La forma abreviada de la clave pública asociada a este ensamblado con nombre seguro. Todos los ensamblados almacenados en la GAC deben tener un nombre, una versión y una clave pública.|
|`Version`|Obligatorio. Versión del ensamblado.<br /><br /> El número de versión tiene el formato \<*major version*> . \<*minor version*> . \<*build version*> . \<*revision version*> .|
|`Language`|Opcional. El idioma de un ensamblado localizado. El valor predeterminado es `neutral`.|
|`ProcessorArchitecture`|Opcional. El procesador del equipo de destino de esta instalación. El valor predeterminado es `msil`.|

## <a name="externalcheck"></a>ExternalCheck
 Este elemento es un elemento secundario opcional de `InstallChecks` . Para cada instancia de `ExternalCheck` , el programa previo ejecutará el programa externo con nombre en un proceso independiente y almacenará su código de salida en la propiedad indicada por `Property` . `ExternalCheck`es útil para implementar comprobaciones de dependencia complejas o cuando la única manera de comprobar la existencia de un componente es crear una instancia de él.

 `ExternalCheck`no contiene ningún elemento y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`Property`|Obligatorio. Nombre de la propiedad en la que se va a almacenar el resultado. Se puede hacer referencia a esta propiedad desde una prueba debajo del `InstallConditions` elemento, que es un elemento secundario del `Command` elemento. Para obtener más información, consulte [Elemento \<Commands>](../deployment/commands-element-bootstrapper.md).|
|`PackageFile`|Obligatorio. Programa externo que se va a ejecutar. El programa debe formar parte del paquete de distribución del programa de instalación.|
|`Arguments`|Opcional. Proporciona argumentos de línea de comandos al ejecutable denominado por `PackageFile` .|

## <a name="filecheck"></a>FileCheck
 Este elemento es un elemento secundario opcional de `InstallChecks` . Para cada instancia de `FileCheck` , el programa previo determinará si existe el archivo con nombre y devolverá el número de versión del archivo. Si el archivo no tiene un número de versión, el arranque establece la propiedad denominada por `Property` en 0. Si el archivo no existe, `Property` no se establece en ningún valor.

 `FileCheck`no contiene ningún elemento y tiene los atributos siguientes.

| Atributo | Descripción |
|-----------------| - |
| `Property` | Obligatorio. Nombre de la propiedad en la que se va a almacenar el resultado. Se puede hacer referencia a esta propiedad desde una prueba debajo del `InstallConditions` elemento, que es un elemento secundario del `Command` elemento. Para obtener más información, consulte [Elemento \<Commands>](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Obligatorio. Nombre del archivo que se va a buscar. |
| `SearchPath` | Obligatorio. Disco o carpeta en la que se va a buscar el archivo. Debe ser una ruta de acceso relativa si `SpecialFolder` está asignada; en caso contrario, debe ser una ruta de acceso absoluta. |
| `SpecialFolder` | Opcional. Una carpeta que tiene una importancia especial en Windows o en [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . El valor predeterminado es interpretar `SearchPath` como una ruta de acceso absoluta. Los valores válidos incluyen los siguientes:<br /><br /> `AppDataFolder`. La carpeta de datos de la aplicación para esta [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación; específica del usuario actual.<br /><br /> `CommonAppDataFolder`. La carpeta de datos de la aplicación que utilizan todos los usuarios.<br /><br /> `CommonFilesFolder`. Carpeta de archivos comunes del usuario actual.<br /><br /> `LocalDataAppFolder`. Carpeta de datos para aplicaciones no móviles.<br /><br /> `ProgramFilesFolder`. La carpeta de archivos de programa estándar para aplicaciones de 32 bits.<br /><br /> `StartUpFolder`. La carpeta que contiene todas las aplicaciones que se inician al iniciar el sistema.<br /><br /> `SystemFolder`. La carpeta que contiene los archivos DLL del sistema de 32 bits.<br /><br /> `WindowsFolder`. La carpeta que contiene la instalación del sistema de Windows.<br /><br /> `WindowsVolume`. La unidad o partición que contiene la instalación del sistema de Windows. |
| `SearchDepth` | Opcional. La profundidad con la que se van a buscar en las subcarpetas del archivo con nombre. La búsqueda se realiza con prioridad a la profundidad. El valor predeterminado es 0, que restringe la búsqueda a la carpeta de nivel superior especificada por `SpecialFolder` y **SearchPath**. |

## <a name="msiproductcheck"></a>MsiProductCheck
 Este elemento es un elemento secundario opcional de `InstallChecks` . Para cada instancia de `MsiProductCheck` , el programa previo comprueba para ver si la instalación de Microsoft Windows Installer especificada se ha ejecutado hasta que se completa. El valor de la propiedad se establece en función del estado del producto instalado. Un valor positivo indica que el producto está instalado, 0 o-1 indica que no está instalado. (Consulte la función MsiQueryFeatureState del SDK de Windows Installer para obtener más información). . Si Windows Installer no está instalado en el equipo, `Property` no se establece.

 `MsiProductCheck`no contiene ningún elemento y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`Property`|Obligatorio. Nombre de la propiedad en la que se va a almacenar el resultado. Se puede hacer referencia a esta propiedad desde una prueba debajo del `InstallConditions` elemento, que es un elemento secundario del `Command` elemento. Para obtener más información, consulte [Elemento \<Commands>](../deployment/commands-element-bootstrapper.md).|
|`Product`|Obligatorio. GUID del producto instalado.|
|`Feature`|Opcional. GUID de una característica específica de la aplicación instalada.|

## <a name="registrycheck"></a>RegistryCheck
 Este elemento es un elemento secundario opcional de `InstallChecks` . Para cada instancia de `RegistryCheck` , el programa previo comprueba para ver si existe la clave del registro especificada, o si tiene el valor indicado.

 `RegistryCheck`no contiene ningún elemento y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`Property`|Obligatorio. Nombre de la propiedad en la que se va a almacenar el resultado. Se puede hacer referencia a esta propiedad desde una prueba debajo del `InstallConditions` elemento, que es un elemento secundario del `Command` elemento. Para obtener más información, consulte [Elemento \<Commands>](../deployment/commands-element-bootstrapper.md).|
|`Key`|Obligatorio. Nombre de la clave del Registro.|
|`Value`|Opcional. Nombre del valor del registro que se va a recuperar. El valor predeterminado es devolver el texto del valor predeterminado. `Value`debe ser una cadena o un valor DWORD.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 Este elemento es un elemento secundario opcional de `InstallChecks` . Para cada instancia de `RegistryFileCheck` , el programa previo recupera la versión del archivo especificado y, en primer lugar, intenta recuperar la ruta de acceso al archivo de la clave del registro especificada. Esto es especialmente útil si desea buscar un archivo en un directorio especificado como un valor en el registro.

 `RegistryFileCheck`no contiene ningún elemento y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`Property`|Obligatorio. Nombre de la propiedad en la que se va a almacenar el resultado. Se puede hacer referencia a esta propiedad desde una prueba debajo del `InstallConditions` elemento, que es un elemento secundario del `Command` elemento. Para obtener más información, consulte [Elemento \<Commands>](../deployment/commands-element-bootstrapper.md).|
|`Key`|Obligatorio. Nombre de la clave del Registro. Su valor se interpreta como la ruta de acceso a un archivo, a menos que `File` se establezca el atributo. Si esta clave no existe, `Property` no se establece.|
|`Value`|Opcional. Nombre del valor del registro que se va a recuperar. El valor predeterminado es devolver el texto del valor predeterminado. `Value`debe ser una cadena.|
|`FileName`|Opcional. Nombre de un archivo. Si se especifica, se supone que el valor obtenido de la clave del registro es una ruta de acceso de directorio y se le anexa este nombre. Si no se especifica, se supone que el valor devuelto del registro es la ruta de acceso completa a un archivo.|
|`SearchDepth`|Opcional. La profundidad con la que se van a buscar en las subcarpetas del archivo con nombre. La búsqueda se realiza con prioridad a la profundidad. El valor predeterminado es 0, que restringe la búsqueda a la carpeta de nivel superior especificada por el valor de la clave del registro.|

## <a name="remarks"></a>Comentarios
 Mientras que los elementos `InstallChecks` que hay debajo definen las pruebas que se van a ejecutar, no las ejecutan. Para ejecutar las pruebas, debe crear `Command` elementos debajo del `Commands` elemento.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra el `InstallChecks` elemento tal como se usa en el archivo de producto para el .NET Framework.

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 Cuando `InstallChecks` se evalúan, generan propiedades. Utilizará las propiedades `InstallConditions` para determinar si un paquete debe instalar, omitir o producir un error. En la tabla siguiente se enumeran los siguientes `InstallConditions` elementos:

|Condición|Descripción|
|-|-|
|`FailIf`|Si una `FailIf` condición se evalúa como true, se producirá un error en el paquete. El resto de las condiciones no se evaluarán.|
|`BypassIf`|Si una `BypassIf` condición se evalúa como true, se omitirá el paquete. El resto de las condiciones no se evaluarán.|

## <a name="predefined-properties"></a>Propiedades predefinidas
 En la tabla siguiente se enumeran los `BypassIf` `FailIf` elementos y:

|Propiedad|Notas|Valores posibles|
|--------------|-----------|---------------------|
|`Version9X`|Número de versión de un sistema operativo Windows 9X.|4,10 = Windows 98|
|`VersionNT`|Número de versión de un sistema operativo basado en Windows NT.|Major.Minor.ServicePack<br /><br /> 5,0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|Número de versión de un sistema operativo basado en Windows NT de 64 bits.|Igual que se mencionó anteriormente.|
|`VersionMsi`|Número de versión del servicio Windows Installer.|2,0 = Windows Installer 2,0|
|`AdminUser`|Especifica si un usuario tiene privilegios de administrador en un sistema operativo basado en Windows NT.|0 = sin privilegios de administrador<br /><br /> 1 = privilegios de administrador|

 Por ejemplo, para bloquear la instalación en un equipo que ejecuta Windows 95, use código como el siguiente:

```xml
<!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

## <a name="see-also"></a>Vea también
- [\<Commands>Element](../deployment/commands-element-bootstrapper.md)
- [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)