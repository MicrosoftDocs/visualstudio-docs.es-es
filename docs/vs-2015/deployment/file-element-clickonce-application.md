---
title: '&lt;file &gt; (elemento, aplicación ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88fce548d5adbd6d4dc930db767fd3e52690490b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148778"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;file &gt; (elemento, aplicación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica todos los archivos no ensamblados descargados y utilizados por la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 El elemento `file` es opcional. El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`name`|Necesario. Identifica el nombre del archivo.|  
|`size`|Necesario. Especifica el tamaño, en bytes, del archivo.|  
|`group`|Opcional, si el `optional` atributo no se especifica o se establece en `false` ; es obligatorio si `optional` es `true` . Nombre del grupo al que pertenece este archivo. El nombre puede ser cualquier valor de cadena Unicode elegido por el desarrollador y se usa para descargar archivos a petición con la <xref:System.Deployment.Application.ApplicationDeployment> clase.|  
|`optional`|Opcional. Especifica si este archivo debe descargarse la primera vez que se ejecuta la aplicación, o si el archivo debe residir solo en el servidor hasta que la aplicación lo solicite a petición. Si `false` es o no está definido, el archivo se descarga cuando la aplicación se ejecuta o se instala por primera vez. Si es `true` , `group` se debe especificar para que el manifiesto de aplicación sea válido. `optional` no puede ser true si `writeableType` se especifica con el valor `applicationData` .|  
|`writeableType`|Opcional. Especifica que este archivo es un archivo de datos. Actualmente, el único valor válido es: `applicationData`.|  
  
## <a name="typelib"></a>typelib  
 El `typelib` elemento es un elemento secundario opcional del elemento File. El elemento describe la biblioteca de tipos que pertenece al componente COM. El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`tlbid`|Necesario. GUID asignado a la biblioteca de tipos.|  
|`version`|Necesario. Número de versión de la biblioteca de tipos.|  
|`helpdir`|Necesario. Directorio que contiene los archivos de ayuda del componente. Puede ser de longitud cero.|  
|`resourceid`|Opcional. Representación de cadena hexadecimal del identificador de configuración regional (LCID). Es de uno a cuatro dígitos hexadecimales sin un prefijo 0x y sin ceros a la izquierda. El LCID puede tener un identificador de subidioma neutro.|  
|`flags`|Opcional. Representación de cadena de las marcas de la biblioteca de tipos para esta biblioteca de tipos. En concreto, debe ser "restricted", "CONTROL", "HIDDEN" y "HASDISKIMAGE".|  
  
## <a name="comclass"></a>comclase  
 El `comClass` elemento es un elemento secundario opcional del `file` elemento, pero es necesario si la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación contiene un componente com que pretende implementar con com sin registro. El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`clsid`|Necesario. IDENTIFICADOR de clase del componente COM expresado como un GUID.|  
|`description`|Opcional. El nombre de la clase.|  
|`threadingModel`|Opcional. Modelo de subprocesos utilizado por las clases COM en proceso. Si esta propiedad es null, no se utiliza ningún modelo de subprocesos. El componente se crea en el subproceso principal del cliente y las referencias de otros subprocesos se serializan en este subproceso. En la lista siguiente se muestran los valores válidos:<br /><br /> `Apartment`, `Free`, `Both` y `Neutral`.|  
|`tlbid`|Opcional. GUID de la biblioteca de tipos para este componente COM.|  
|`progid`|Opcional. Identificador de programación dependiente de la versión asociado al componente COM. El formato de `ProgID` es `<vendor>.<component>.<version>` .|  
|`miscStatus`|Opcional. Los duplicados en el ensamblado proporcionan la información proporcionada por la `MiscStatus` clave del registro. Si no se encuentran los valores de los `miscStatusIcon` `miscStatusContent` atributos,, `miscStatusDocprint` o `miscStatusThumbnail` , se usa el valor predeterminado correspondiente enumerado en `miscStatus` para los atributos que faltan. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores de clave del registro.|  
|`miscStatusIcon`|Opcional. Los duplicados en el ensamblado proporcionan la información proporcionada por DVASPECT_ICON. Puede proporcionar un icono de un objeto. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `Miscstatus` valores de clave del registro.|  
|`miscStatusContent`|Opcional. Los duplicados en el ensamblado proporcionan la información proporcionada por DVASPECT_CONTENT. Puede proporcionar un documento compuesto que se pueda mostrar en una pantalla o una impresora. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores de clave del registro.|  
|`miscStatusDocPrint`|Opcional. Los duplicados en el ensamblado proporcionan la información proporcionada por DVASPECT_DOCPRINT. Puede proporcionar una representación de objeto que se pueda mostrar en la pantalla como si se imprimiera en una impresora. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores de clave del registro.|  
|`miscStatusThumbnail`|Opcional. Los duplicados de un ensamblado manifiestan la información proporcionada por DVASPECT_THUMBNAIL. Puede proporcionar una miniatura de un objeto que se pueda mostrar en una herramienta de exploración. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores de clave del registro.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 El `comInterfaceExternalProxyStub` elemento es un elemento secundario opcional del `file` elemento, pero puede ser necesario si la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación contiene un componente com que pretende implementar con com sin registro. El elemento contiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`iid`|Necesario. IDENTIFICADOR de interfaz (IID) que sirve este proxy. El IID debe contener llaves.|  
|`baseInterface`|Opcional. IID de la interfaz de la que se deriva la interfaz a la que hace referencia `iid` .|  
|`numMethods`|Opcional. El número de métodos implementados por la interfaz.|  
|`name`|Opcional. El nombre de la interfaz tal y como aparecerá en el código.|  
|`tlbid`|Opcional. Biblioteca de tipos que contiene la descripción de la interfaz especificada por el `iid` atributo.|  
|`proxyStubClass32`|Opcional. Asigna un IID a un CLSID en dll de proxy de 32 bits.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 El `comInterfaceProxyStub` elemento es un elemento secundario opcional del `file` elemento, pero puede ser necesario si la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación contiene un componente com que pretende implementar con com sin registro. El elemento contiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`iid`|Necesario. IDENTIFICADOR de interfaz (IID) que sirve este proxy. El IID debe contener llaves.|  
|`baseInterface`|Opcional. IID de la interfaz de la que se deriva la interfaz a la que hace referencia `iid` .|  
|`numMethods`|Opcional. El número de métodos implementados por la interfaz.|  
|`Name`|Opcional. El nombre de la interfaz tal y como aparecerá en el código.|  
|`Tlbid`|Opcional. Biblioteca de tipos que contiene la descripción de la interfaz especificada por el `iid` atributo.|  
|`proxyStubClass32`|Opcional. Asigna un IID a un CLSID en dll de proxy de 32 bits.|  
|`threadingModel`|Opcional. Opcional. Modelo de subprocesos utilizado por las clases COM en proceso. Si esta propiedad es null, no se utiliza ningún modelo de subprocesos. El componente se crea en el subproceso principal del cliente y las referencias de otros subprocesos se serializan en este subproceso. En la lista siguiente se muestran los valores válidos:<br /><br /> `Apartment`, `Free`, `Both` y `Neutral`.|  
  
## <a name="windowclass"></a>windowClass  
 El `windowClass` elemento es un elemento secundario opcional del `file` elemento, pero puede ser necesario si la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación contiene un componente com que pretende implementar con com sin registro. El elemento hace referencia a una clase de ventana definida por el componente COM al que se le debe aplicar una versión. El elemento contiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`versioned`|Opcional. Controla si el nombre de la clase de ventana interna utilizada en el registro contiene la versión del ensamblado que contiene la clase de ventana. El valor de este atributo puede ser `yes` o `no` . El valor predeterminado es `yes`. El valor `no` solo se debe usar si la misma clase de ventana está definida por un componente en paralelo y un componente no en paralelo equivalente y desea tratarlos como la misma clase de ventana... Tenga en cuenta que se aplican las reglas habituales sobre el registro de clases de ventana, solo el primer componente que registra la clase de ventana podrá registrarla, ya que no tiene aplicada una versión.|  
  
## <a name="hash"></a>hash  
 El `hash` elemento es un elemento secundario opcional del `file` elemento. El elemento `hash` no tiene atributos.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] utiliza un hash algorítmico de todos los archivos de una aplicación como una comprobación de seguridad, para asegurarse de que ninguno de los archivos se cambió después de la implementación. Si `hash` no se incluye el elemento, no se realizará esta comprobación. Por lo tanto, `hash` no se recomienda omitir el elemento.  
  
 Si un manifiesto contiene un archivo que no tiene hash, no se puede firmar digitalmente, porque los usuarios no pueden comprobar el contenido de un archivo sin hash.  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 El `dsig:Transforms` elemento es un elemento secundario necesario del `hash` elemento. El elemento `dsig:Transforms` no tiene atributos.  
  
## <a name="dsigtransform"></a>dsig: transformación  
 El `dsig:Transform` elemento es un elemento secundario necesario del `dsig:Transforms` elemento. El elemento `dsig:Transform` tiene los atributos siguientes:  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Algorithm`|Algoritmo usado para calcular el Resumen de este archivo. Actualmente, el único valor utilizado por [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 El `dsig:DigestMethod` elemento es un elemento secundario necesario del `hash` elemento. El elemento `dsig:DigestMethod` tiene los atributos siguientes:  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Algorithm`|Algoritmo usado para calcular el Resumen de este archivo. Actualmente, el único valor utilizado por [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 El `dsig:DigestValue` elemento es un elemento secundario necesario del `hash` elemento. El elemento `dsig:DigestValue` no tiene atributos. Su valor de texto es el hash calculado para el archivo especificado.  
  
## <a name="remarks"></a>Comentarios  
 Este elemento identifica todos los archivos no ensamblados que componen la aplicación y, en particular, los valores hash para la comprobación de archivos. Este elemento también puede incluir datos de aislamiento del modelo de objetos componentes (COM) asociados al archivo. Si un archivo cambia, el archivo de manifiesto de aplicación también debe actualizarse para reflejar el cambio.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestran `file` los elementos de un manifiesto de aplicación para una aplicación implementada mediante [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
```  
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
  
## <a name="see-also"></a>Consulte también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
