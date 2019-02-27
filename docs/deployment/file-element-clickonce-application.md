---
title: '&lt;archivo&gt; elemento (aplicación ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4152482f404596e1d97a94a12890b4c5b298794
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604228"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;archivo&gt; elemento (aplicación ClickOnce)
Identifica todos los archivos nonassembly descargado y usado por la aplicación.

## <a name="syntax"></a>Sintaxis

```xml
<file
    name
    size
    group
    optional
    writeableType
>
    <typelib
        tlbid
        version
        helpdir
        resourceid
        flags
    />
    <comClass
        clsid
        description
        threadingModel
        tlbid
        progid
        miscStatus
        miscStatusIcon
        miscStatusContent
        miscStatusDocPrint
        miscStatusThumbnail
    />
    <comInterfaceExternalProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <comInterfaceProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <windowClass
        versioned
    />
</file>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `file` es opcional. El elemento tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`name`|Obligatorio. Identifica el nombre del archivo.|
|`size`|Obligatorio. Especifica el tamaño, en bytes, del archivo.|
|`group`|Opcional, si la `optional` atributo no se especifica o se establece en `false`; es necesario si `optional` es `true`. El nombre del grupo al que pertenece este archivo. El nombre puede ser cualquier valor de cadena Unicode elegido por el desarrollador y se usa para descargar archivos a petición con la <xref:System.Deployment.Application.ApplicationDeployment> clase.|
|`optional`|Opcional. Especifica si este archivo debe descargar cuando la aplicación es la primera ejecución, o si el archivo debe residir únicamente en el servidor hasta que la aplicación lo solicita a petición. Si `false` o undefined, el archivo se descarga cuando la aplicación se ejecuta o se instala en primer lugar. Si `true`, un `group` debe especificarse para que el manifiesto de aplicación sea válido. `optional` no puede ser true si `writeableType` se especifica con el valor `applicationData`.|
|`writeableType`|Opcional. Especifica que este archivo es un archivo de datos. Actualmente, el único valor válido es: `applicationData`.|

## <a name="typelib"></a>typelib
 El `typelib` elemento es un elemento secundario opcional del elemento file. El elemento describe la biblioteca de tipos al que pertenece el componente COM. El elemento tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`tlbid`|Obligatorio. El GUID asignado a la biblioteca de tipos.|
|`version`|Obligatorio. El número de versión de la biblioteca de tipos.|
|`helpdir`|Obligatorio. El directorio que contiene los archivos de ayuda para el componente. Puede ser de longitud cero.|
|`resourceid`|Opcional. La representación de cadena hexadecimal del identificador de configuración regional (LCID). Es uno a cuatro dígitos hexadecimales sin un prefijo 0 x y sin ceros iniciales. El LCID puede tener un identificador de subidioma neutro.|
|`flags`|Opcional. La representación de cadena de los marcadores de biblioteca de tipos para esta biblioteca de tipos. En concreto, debe ser uno de "RESTRICTED", "CONTROL", "HIDDEN" y "HASDISKIMAGE".|

## <a name="comclass"></a>comClass
 El `comClass` elemento es un elemento secundario opcional de la `file` elemento, pero es necesario si la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación contiene un componente COM intenta implementar mediante COM sin registro. El elemento tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`clsid`|Obligatorio. El identificador de clase del componente COM expresado como un GUID.|
|`description`|Opcional. Nombre de la clase.|
|`threadingModel`|Opcional. El modelo de subprocesos utilizado por las clases de COM en proceso. Si esta propiedad es null, no se utiliza ningún modelo de subprocesos. El componente se crea en el subproceso principal del cliente y las llamadas de otros subprocesos se calculan las referencias a este subproceso. La siguiente lista muestra los valores válidos:<br /><br /> `Apartment`, `Free`, `Both`y `Neutral`.|
|`tlbid`|Opcional. GUID de la biblioteca de tipos para este componente COM.|
|`progid`|Opcional. Identificador de programación dependientes de la versión asociado al componente COM. El formato de un `ProgID` es `<vendor>.<component>.<version>`.|
|`miscStatus`|Opcional. Duplica en el ensamblado de manifiesto de la información proporcionada por el `MiscStatus` clave del registro. Si los valores de la `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, o `miscStatusThumbnail` no se encuentra el atributo, el valor predeterminado correspondiente que aparece en `miscStatus` se usa para los atributos que faltan. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores clave del registro.|
|`miscStatusIcon`|Opcional. Duplica en el ensamblado de manifiesto de la información proporcionada por DVASPECT_ICON. Puede proporcionar un icono de un objeto. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `Miscstatus` valores clave del registro.|
|`miscStatusContent`|Opcional. Los duplicados en el ensamblado de manifiesto de la información proporcionada por DVASPECT_CONTENT. Puede proporcionar un documento compuesto que se puede mostrar para una pantalla o impresora. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores clave del registro.|
|`miscStatusDocPrint`|Opcional. Los duplicados en el ensamblado de manifiesto de la información proporcionada por DVASPECT_DOCPRINT. Puede proporcionar una representación de objeto que se puede mostrar en la pantalla como si imprime en una impresora. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores clave del registro.|
|`miscStatusThumbnail`|Opcional. Duplicados en un ensamblado de manifiesto la información proporcionada por DVASPECT_THUMBNAIL. Puede proporcionar una miniatura de un objeto que se puede mostrar en una herramienta de exploración. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores clave del registro.|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 El `comInterfaceExternalProxyStub` elemento es un elemento secundario opcional de la `file` elemento, pero puede ser necesario si la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación contiene un componente COM intenta implementar mediante COM sin registro. El elemento contiene los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|`iid`|Obligatorio. La interfaz de identificador (IID) que atienden a este proxy. El IID debe tener las llaves que lo rodea.|
|`baseInterface`|Opcional. El IID de la interfaz desde la que hace referencia la interfaz `iid` derivada.|
|`numMethods`|Opcional. El número de métodos implementados por la interfaz.|
|`name`|Opcional. El nombre de la interfaz tal y como aparecerá en el código.|
|`tlbid`|Opcional. La biblioteca de tipos que contiene la descripción de la interfaz especificada por el `iid` atributo.|
|`proxyStubClass32`|Opcional. Asigna un IID a un CLSID en archivos DLL de proxy de 32 bits.|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 El `comInterfaceProxyStub` elemento es un elemento secundario opcional de la `file` elemento, pero puede ser necesario si la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación contiene un componente COM intenta implementar mediante COM sin registro. El elemento contiene los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|`iid`|Obligatorio. La interfaz de identificador (IID) que atienden a este proxy. El IID debe tener las llaves que lo rodea.|
|`baseInterface`|Opcional. El IID de la interfaz desde la que hace referencia la interfaz `iid` derivada.|
|`numMethods`|Opcional. El número de métodos implementados por la interfaz.|
|`Name`|Opcional. El nombre de la interfaz tal y como aparecerá en el código.|
|`Tlbid`|Opcional. La biblioteca de tipos que contiene la descripción de la interfaz especificada por el `iid` atributo.|
|`proxyStubClass32`|Opcional. Asigna un IID a un CLSID en archivos DLL de proxy de 32 bits.|
|`threadingModel`|Opcional. Opcional. El modelo de subprocesos utilizado por las clases de COM en proceso. Si esta propiedad es null, no se utiliza ningún modelo de subprocesos. El componente se crea en el subproceso principal del cliente y las llamadas de otros subprocesos se calculan las referencias a este subproceso. La siguiente lista muestra los valores válidos:<br /><br /> `Apartment`, `Free`, `Both`y `Neutral`.|

## <a name="windowclass"></a>windowClass
 El `windowClass` elemento es un elemento secundario opcional de la `file` elemento, pero puede ser necesario si la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación contiene un componente COM intenta implementar mediante COM sin registro. El elemento hace referencia a una clase de ventana definida por el componente COM que debe tener una versión que se aplican a él. El elemento contiene los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|`versioned`|Opcional. Controles de la ventana interna que la clase utilizada en el registro de nombre contiene la versión del ensamblado que contiene la clase de ventana. El valor de este atributo puede ser `yes` o `no`. De manera predeterminada, es `yes`. El valor `no` solo debe usarse si la misma clase de ventana se define mediante un componente en paralelo y un componente no-side-by-side equivalente y desea tratarlos como la misma clase de ventana. Tenga en cuenta que se aplican las reglas habituales sobre el registro de la clase de ventana: solo el primer componente que se registra la clase de ventana podrán registrarla, porque no tiene una versión que se aplica a él.|

## <a name="hash"></a>hash
 El `hash` elemento es un elemento secundario opcional de la `file` elemento. El elemento `hash` no tiene atributos.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utiliza un valor hash algorítmico de todos los archivos en una aplicación como una comprobación de seguridad para asegurarse de que ninguno de los archivos se han modificado después de la implementación. Si el `hash` elemento no se incluye, no se realizará esta comprobación. Por lo tanto, si se omite el `hash` elemento no se recomienda.

 Si un manifiesto contiene un archivo que no está en hash, ese manifiesto no puede ser digitalmente firmado, ya que los usuarios no pueden comprobar el contenido de un archivo de este tipo.

## <a name="dsigtransforms"></a>dsig:Transforms
 El `dsig:Transforms` elemento es un elemento secundario necesario de la `hash` elemento. El elemento `dsig:Transforms` no tiene atributos.

## <a name="dsigtransform"></a>dsig: Transform
 El `dsig:Transform` elemento es un elemento secundario necesario de la `dsig:Transforms` elemento. El elemento `dsig:Transform` tiene los atributos siguientes:


| Atributo | Descripción |
|-------------| - |
| `Algorithm` | El algoritmo utilizado para calcular la síntesis de este archivo. Actualmente el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity`. |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 El `dsig:DigestMethod` elemento es un elemento secundario necesario de la `hash` elemento. El elemento `dsig:DigestMethod` tiene los atributos siguientes:


| Atributo | Descripción |
|-------------| - |
| `Algorithm` | El algoritmo utilizado para calcular la síntesis de este archivo. Actualmente el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1`. |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 El `dsig:DigestValue` elemento es un elemento secundario necesario de la `hash` elemento. El elemento `dsig:DigestValue` no tiene atributos. Su valor de texto es el hash calculado para el archivo especificado.

## <a name="remarks"></a>Comentarios
 Este elemento identifica todos los archivos nonassembly que componen la aplicación y, en concreto, los valores hash de archivo de comprobación. Este elemento también puede incluir datos de aislamiento del modelo de objetos componentes (COM) asociados con el archivo. Si un archivo cambia, el archivo de manifiesto de aplicación también debe actualizarse para reflejar el cambio.

## <a name="example"></a>Ejemplo
 El siguiente ejemplo de código ilustra `file` elementos en una aplicación de manifiesto para una aplicación implementada mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

```xml
<file name="Icon.ico" size="9216">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>
  </hash>
</file>
```

## <a name="see-also"></a>Vea también
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)