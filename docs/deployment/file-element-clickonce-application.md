---
title: '&lt;archivo&gt; elemento (aplicación ClickOnce) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1e744071219426c751576f8ca781ad27dfedb61
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815865"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;archivo&gt; elemento (aplicación ClickOnce)
Identifica todos los archivos nonassembly descargados y utilizados por la aplicación.  
  
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
 El elemento `file` es opcional. El elemento tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`name`|Requerido. Identifica el nombre del archivo.|  
|`size`|Requerido. Especifica el tamaño, en bytes, del archivo.|  
|`group`|Opcional, si la `optional` atributo no se especifica o se establece en `false`; es necesario si `optional` es `true`. El nombre del grupo al que pertenece este archivo. El nombre puede ser cualquier valor de cadena de Unicode elegido por el desarrollador y se utiliza para la descarga de archivos a petición con la <xref:System.Deployment.Application.ApplicationDeployment> clase.|  
|`optional`|Opcional. Especifica si este archivo debe ser descarga cuando la aplicación es la primera ejecución, o si el archivo debe residir en el servidor hasta que la aplicación lo solicite a petición. Si `false` o sin definir, el archivo se descarga cuando la aplicación se ejecuta o se instala en primer lugar. Si `true`, un `group` debe especificarse para que el manifiesto de aplicación sea válido. `optional` no puede ser true si `writeableType` se especifica con el valor `applicationData`.|  
|`writeableType`|Opcional. Especifica que este archivo es un archivo de datos. Actualmente, el único valor válido es `applicationData`.|  
  
## <a name="typelib"></a>biblioteca de tipos  
 El `typelib` elemento es un elemento secundario opcional del elemento file. El elemento describe la biblioteca de tipos a la que pertenece el componente COM. El elemento tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`tlbid`|Requerido. El GUID asignado a la biblioteca de tipos.|  
|`version`|Requerido. El número de versión de la biblioteca de tipos.|  
|`helpdir`|Requerido. El directorio que contiene los archivos de ayuda para el componente. Puede ser de longitud cero.|  
|`resourceid`|Opcional. La representación de cadena hexadecimal del identificador de configuración regional (LCID). Es uno a cuatro dígitos hexadecimales sin un prefijo 0 x y sin ceros a la izquierda. El LCID puede tener un identificador de sublenguaje neutro.|  
|`flags`|Opcional. La representación de cadena de los marcadores de biblioteca de tipos para esta biblioteca de tipos. En concreto, debe ser uno de "RESTRICTED", "CONTROL", "HIDDEN" y "HASDISKIMAGE".|  
  
## <a name="comclass"></a>comClass  
 El `comClass` elemento es un elemento secundario opcional de la `file` elemento, pero es necesario si la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación contiene un componente COM intenta implementar mediante COM sin registro. El elemento tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`clsid`|Requerido. El identificador de clase del componente COM expresado como un GUID.|  
|`description`|Opcional. Nombre de la clase.|  
|`threadingModel`|Opcional. El modelo de subprocesos utilizado por las clases COM en el proceso. Si esta propiedad es null, no se utiliza ningún modelo de subprocesamiento. El componente se crea en el subproceso principal del cliente y llamadas de otros subprocesos se calculan las referencias a este subproceso. En la lista siguiente se muestra los valores válidos:<br /><br /> `Apartment`, `Free`, `Both` y `Neutral`.|  
|`tlbid`|Opcional. GUID de la biblioteca de tipos para este componente COM.|  
|`progid`|Opcional. Identificador de programación dependientes de la versión asociado al componente COM. El formato de un `ProgID` es `<vendor>.<component>.<version>`.|  
|`miscStatus`|Opcional. Duplica en el ensamblado de manifiesto de la información proporcionada por el `MiscStatus` clave del registro. Si los valores para la `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, o `miscStatusThumbnail` no se encuentran los atributos, el valor predeterminado correspondiente aparece en `miscStatus` se usa para los atributos que faltan. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores clave del registro.|  
|`miscStatusIcon`|Opcional. Duplica en el ensamblado de manifiesto de la información proporcionada por DVASPECT_ICON. Puede proporcionar un icono de un objeto. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `Miscstatus` valores clave del registro.|  
|`miscStatusContent`|Opcional. Duplica en el ensamblado de manifiesto de la información proporcionada por DVASPECT_CONTENT. Puede proporcionar un documento compuesto que se pueden mostrar en una pantalla o impresora. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores clave del registro.|  
|`miscStatusDocPrint`|Opcional. Duplica en el ensamblado de manifiesto de la información proporcionada por DVASPECT_DOCPRINT. Puede proporcionar una representación de objeto que se pueden mostrar en la pantalla como si imprime en una impresora. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores clave del registro.|  
|`miscStatusThumbnail`|Opcional. Duplica en un ensamblado de manifiesto de la información proporcionada por DVASPECT_THUMBNAIL. Puede proporcionar una vista en miniatura de un objeto que puede mostrarse en una herramienta de exploración. El valor puede ser una lista delimitada por comas de los valores de atributo de la tabla siguiente. Puede usar este atributo si la clase COM es una clase OCX que requiere `MiscStatus` valores clave del registro.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 El `comInterfaceExternalProxyStub` elemento es un elemento secundario opcional de la `file` elemento, pero puede ser necesario si la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación contiene un componente COM intenta implementar mediante COM sin registro. El elemento contiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`iid`|Requerido. El identificador de interfaz (IID) que ofrece este proxy. El IID debe tener llaves.|  
|`baseInterface`|Opcional. El IID de la interfaz desde la que hace referencia la interfaz `iid` se deriva.|  
|`numMethods`|Opcional. El número de métodos implementados por la interfaz.|  
|`name`|Opcional. El nombre de la interfaz tal y como aparecerá en el código.|  
|`tlbid`|Opcional. La biblioteca de tipos que contiene la descripción de la interfaz especificada por el `iid` atributo.|  
|`proxyStubClass32`|Opcional. Asigna un IID a un CLSID en archivos DLL de proxy de 32 bits.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 El `comInterfaceProxyStub` elemento es un elemento secundario opcional de la `file` elemento, pero puede ser necesario si la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación contiene un componente COM intenta implementar mediante COM sin registro. El elemento contiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`iid`|Requerido. El identificador de interfaz (IID) que ofrece este proxy. El IID debe tener llaves.|  
|`baseInterface`|Opcional. El IID de la interfaz desde la que hace referencia la interfaz `iid` se deriva.|  
|`numMethods`|Opcional. El número de métodos implementados por la interfaz.|  
|`Name`|Opcional. El nombre de la interfaz tal y como aparecerá en el código.|  
|`Tlbid`|Opcional. La biblioteca de tipos que contiene la descripción de la interfaz especificada por el `iid` atributo.|  
|`proxyStubClass32`|Opcional. Asigna un IID a un CLSID en archivos DLL de proxy de 32 bits.|  
|`threadingModel`|Opcional. Opcional. El modelo de subprocesos utilizado por las clases COM en el proceso. Si esta propiedad es null, no se utiliza ningún modelo de subprocesamiento. El componente se crea en el subproceso principal del cliente y llamadas de otros subprocesos se calculan las referencias a este subproceso. En la lista siguiente se muestra los valores válidos:<br /><br /> `Apartment`, `Free`, `Both` y `Neutral`.|  
  
## <a name="windowclass"></a>windowClass  
 El `windowClass` elemento es un elemento secundario opcional de la `file` elemento, pero puede ser necesario si la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación contiene un componente COM intenta implementar mediante COM sin registro. El elemento hace referencia a una clase de ventana definida por el componente COM que debe tener una versión aplicada a él. El elemento contiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`versioned`|Opcional. Controla si el nombre que se utiliza en el registro de la clase de ventana interna contiene la versión del ensamblado que contiene la clase de ventana. El valor de este atributo puede ser `yes` o `no`. De manera predeterminada, es `yes`. El valor `no` solo debe usarse si la misma clase de ventana se define mediante un componente en paralelo y un componente no en paralelo equivalente y desea tratarlos como la misma clase de ventana. Tenga en cuenta que se aplican las reglas habituales acerca del registro de la clase de ventana: solo el primer componente que se registra la clase de ventana podrán registrar, porque no tiene una versión que se aplican a ella.|  
  
## <a name="hash"></a>hash  
 El `hash` elemento es un elemento secundario opcional de la `file` elemento. El `hash` elemento no tiene atributos.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utiliza un valor hash algorítmico de todos los archivos en una aplicación como una comprobación de seguridad, para asegurarse de que ninguno de los archivos se han modificado después de la implementación. Si el `hash` elemento no se incluye, no se realizará esta comprobación. Por lo tanto, si se omite la `hash` elemento no se recomienda.  
  
 Si un manifiesto contiene un archivo que no está en hash, ese manifiesto no puede ser digitalmente firmado, porque los usuarios no pueden comprobar el contenido de un archivo de este tipo.  
  
## <a name="dsigtransforms"></a>dsig: TRANSFORMS  
 El `dsig:Transforms` elemento es un elemento secundario necesario de la `hash` elemento. El `dsig:Transforms` elemento no tiene atributos.  
  
## <a name="dsigtransform"></a>dsig: Transform  
 El `dsig:Transform` elemento es un elemento secundario necesario de la `dsig:Transforms` elemento. El `dsig:Transform` elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Algorithm`|El algoritmo utilizado para calcular el resumen para este archivo. Actualmente el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 El `dsig:DigestMethod` elemento es un elemento secundario necesario de la `hash` elemento. El `dsig:DigestMethod` elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Algorithm`|El algoritmo utilizado para calcular el resumen para este archivo. Actualmente el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig: DigestValue  
 El `dsig:DigestValue` elemento es un elemento secundario necesario de la `hash` elemento. El `dsig:DigestValue` elemento no tiene atributos. Su valor de texto es el hash calculado para el archivo especificado.  
  
## <a name="remarks"></a>Comentarios  
 Este elemento identifica todos los archivos nonassembly que constituyen la aplicación y, en particular, los valores hash de archivo de comprobación. Este elemento también puede incluir datos de aislamiento de modelo de objetos componentes (COM) asociados al archivo. Si cambia un archivo, el archivo de manifiesto de aplicación también debe actualizarse para reflejar el cambio.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra `file` manifiesto de elementos en una aplicación para una aplicación implementada mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
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
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)