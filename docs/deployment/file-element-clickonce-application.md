---
title: "Elemento &lt;file&gt; (Aplicaci&#243;n ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#file"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<file> (elemento) [manifiesto de aplicación ClickOnce]"
  - "manifiestos [ClickOnce], elemento de archivo"
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# Elemento &lt;file&gt; (Aplicaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica todos los archivos nonassembly descargados y utilizados por la aplicación.  
  
## Sintaxis  
  
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
  
## Elementos y atributos  
 El elemento `file` es opcional.  El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`name`|Obligatorio.  Identifica el nombre del archivo.|  
|`size`|Obligatorio.  Especifica el tamaño del archivo, en bytes.|  
|`group`|Opcional, si el atributo `optional` no se especifica o se establece en `false`; obligatorio si `optional` es `true`.  Nombre del grupo al que pertenece este archivo.  El nombre puede ser cualquier valor de cadena de Unicode elegido por el desarrollador y se utiliza para descargar los archivos a petición con la clase <xref:System.Deployment.Application.ApplicationDeployment>.|  
|`optional`|Opcional.  Especifica si el archivo debe descargarse al iniciar la aplicación por primera vez, o si debe residir únicamente en el servidor hasta que la aplicación lo solicite a petición.  Si es `false` o no está definido, el archivo se descarga cuando se ejecuta o instala la aplicación por primera vez.  Si es `true`, se debe especificar un `group` para que el manifiesto de aplicación sea válido.  `optional` no puede ser true si `writeableType` se especifica con el valor `applicationData`.|  
|`writeableType`|Opcional.  Especifica que este archivo es un archivo de datos.  Actualmente, el único valor válido es `applicationData`.|  
  
## typelib  
 El elemento `typelib` es un elemento secundario opcional del elemento de archivo.  Este elemento describe la biblioteca de tipos que pertenece al componente COM.  El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`tlbid`|Obligatorio.  GUID asignado a la biblioteca de tipos.|  
|`version`|Obligatorio.  Número de versión de la biblioteca de tipos.|  
|`helpdir`|Obligatorio.  Directorio que contiene los archivos de Ayuda del componente.  Puede ser de longitud cero.|  
|`resourceid`|Opcional.  Representación de cadena hexadecimal del identificador de configuración regional \(LCID\).  Presenta de uno a cuatro dígitos hexadecimales sin un prefijo 0x y sin ceros a la izquierda.  El LCID puede tener un identificador de sublenguaje neutro.|  
|`flags`|Opcional.  Representación de cadena de los marcadores de biblioteca de tipos de esta biblioteca de tipos.  Concretamente, debería ser uno de los siguientes: "RESTRICTED", "CONTROL", "HIDDEN" y "HASDISKIMAGE".|  
  
## comClass  
 El elemento `comClass` es un elemento secundario opcional del elemento `file`, pero es obligatorio si la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] contiene un componente COM que intenta implementar mediante COM sin registro.  El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`clsid`|Obligatorio.  Id. de clase del componente COM expresado como un GUID.|  
|`description`|Opcional.  Nombre de la clase.|  
|`threadingModel`|Opcional.  Modelo de subprocesos utilizado por las clases COM en proceso.  Si esta propiedad es null, no se utiliza ningún modelo de subprocesos.  El componente se crea en el subproceso principal del cliente y se calculan las referencias de las llamadas de otros subprocesos para este subproceso.  En la siguiente lista se muestran los valores válidos:<br /><br /> `Apartment`, `Free`, `Both` y `Neutral`.|  
|`tlbid`|Opcional.  GUID de la biblioteca de tipos de este componente COM.|  
|`progid`|Opcional.  Identificador de programación dependiente de la versión asociado al componente COM.  El formato de `ProgID` es `<vendor>.<component>.<version>`.|  
|`miscStatus`|Opcional.  Duplica en el manifiesto del ensamblado la información proporcionada por la clave del Registro `MiscStatus`.  Si no se encuentran valores para los atributos `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint` o `miscStatusThumbnail`, se utiliza el valor predeterminado correspondiente que se muestra en `miscStatus` para los atributos que faltan.  El valor puede ser una lista delimitada por comas de los valores de atributo de la siguiente tabla.  Puede utilizar este atributo si la clase COM es una clase OCX que requiere valores de la clave del Registro `MiscStatus`.|  
|`miscStatusIcon`|Opcional.  Duplica en el manifiesto del ensamblado la información proporcionada por DVASPECT\_ICON.  Puede proporcionar un icono de un objeto.  El valor puede ser una lista delimitada por comas de los valores de atributo de la siguiente tabla.  Puede utilizar este atributo si la clase COM es una clase OCX que requiere valores de la clave del Registro `Miscstatus`.|  
|`miscStatusContent`|Opcional.  Duplica en el manifiesto del ensamblado la información proporcionada por DVASPECT\_CONTENT.  Puede proporcionar un documento compuesto que puede mostrarse en una pantalla o impresora.  El valor puede ser una lista delimitada por comas de los valores de atributo de la siguiente tabla.  Puede utilizar este atributo si la clase COM es una clase OCX que requiere valores de la clave del Registro `MiscStatus`.|  
|`miscStatusDocPrint`|Opcional.  Duplica en el manifiesto del ensamblado la información proporcionada por DVASPECT\_DOCPRINT.  Puede proporcionar una representación de objeto que puede mostrarse en la pantalla como si se hubiese impreso en una impresora.  El valor puede ser una lista delimitada por comas de los valores de atributo de la siguiente tabla.  Puede utilizar este atributo si la clase COM es una clase OCX que requiere valores de la clave del Registro `MiscStatus`.|  
|`miscStatusThumbnail`|Opcional.  Duplica en el manifiesto del ensamblado la información proporcionada por DVASPECT\_THUMBNAIL.  Puede proporcionar una miniatura de un objeto que puede mostrarse en una herramienta de exploración.  El valor puede ser una lista delimitada por comas de los valores de atributo de la siguiente tabla.  Puede utilizar este atributo si la clase COM es una clase OCX que requiere valores de la clave del Registro `MiscStatus`.|  
  
## comInterfaceExternalProxyStub  
 El elemento `comInterfaceExternalProxyStub` es un elemento secundario opcional del elemento `file`, pero puede ser obligatorio si la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] contiene un componente COM que intenta implementar mediante COM sin registro.  El elemento contiene los siguientes atributos.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`iid`|Obligatorio.  Id. de interfaz \(IID\) suministrado por este servidor proxy.  El IID debe estar incluido entre llaves.|  
|`baseInterface`|Opcional.  IID de la interfaz de la que se deriva la interfaz a la que hace referencia `iid`.|  
|`numMethods`|Opcional.  Número de métodos implementados por la interfaz.|  
|`name`|Opcional.  Nombre de la interfaz tal y como aparecerá en el código.|  
|`tlbid`|Opcional.  Biblioteca de tipos que contiene la descripción de la interfaz especificada por el atributo `iid`.|  
|`proxyStubClass32`|Opcional.  Asigna un IID a un CLSID en archivos DLL de proxy de 32 bits.|  
  
## comInterfaceProxyStub  
 El elemento `comInterfaceProxyStub` es un elemento secundario opcional del elemento `file`, pero puede ser obligatorio si la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] contiene un componente COM que intenta implementar mediante COM sin registro.  El elemento contiene los siguientes atributos.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`iid`|Obligatorio.  Id. de interfaz \(IID\) suministrado por este servidor proxy.  El IID debe estar incluido entre llaves.|  
|`baseInterface`|Opcional.  IID de la interfaz de la que se deriva la interfaz a la que hace referencia `iid`.|  
|`numMethods`|Opcional.  Número de métodos implementados por la interfaz.|  
|`Name`|Opcional.  Nombre de la interfaz tal y como aparecerá en el código.|  
|`Tlbid`|Opcional.  Biblioteca de tipos que contiene la descripción de la interfaz especificada por el atributo `iid`.|  
|`proxyStubClass32`|Opcional.  Asigna un IID a un CLSID en archivos DLL de proxy de 32 bits.|  
|`threadingModel`|Opcional.  Opcional.  Modelo de subprocesos utilizado por las clases COM en proceso.  Si esta propiedad es null, no se utiliza ningún modelo de subprocesos.  El componente se crea en el subproceso principal del cliente y se calculan las referencias de las llamadas de otros subprocesos para este subproceso.  En la siguiente lista se muestran los valores válidos:<br /><br /> `Apartment`, `Free`, `Both` y `Neutral`.|  
  
## windowClass  
 El elemento `windowClass` es un elemento secundario opcional del elemento `file`, pero puede ser obligatorio si la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] contiene un componente COM que intenta implementar mediante COM sin registro.  El elemento hace referencia a una clase de ventana definida por el componente COM que debe tener una versión aplicada.  El elemento contiene los siguientes atributos.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`versioned`|Opcional.  Controla si el nombre de la clase de ventana interna utilizada en el registro contiene la versión del ensamblado que contiene la clase de ventana.  El valor de este atributo puede ser `yes` o `no`.  El valor predeterminado es `yes`.  Sólo debe utilizarse el valor `no` si un componente en paralelo y un componente no en paralelo equivalente definen la misma clase de ventana y se desea que estos componentes se consideren la misma clase de ventana.  Tenga en cuenta que se aplican las reglas normales de registro de clase de ventana; sólo el primer componente que registre la clase de ventana podrá registrarla, ya que no tiene una versión aplicada.|  
  
## hash  
 El elemento `hash` es un elemento secundario opcional del elemento `file`.  El elemento `hash` no tiene atributos.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utiliza un valor hash algorítmico de todos los archivos de una aplicación como comprobación de seguridad para asegurarse de que no se modificó ninguno de los archivos después de la implementación.  Si el elemento `hash` no está incluido, no se realizará esta comprobación. En consecuencia, no se recomienda omitir el elemento `hash`.  
  
 Si un manifiesto contiene un archivo al que no se aplica un algoritmo hash, dicho manifiesto no puede estar firmado digitalmente, ya que los usuarios no pueden comprobar el contenido de un archivo al que no se aplicó un algoritmo hash.  
  
## dsig:Transforms  
 El elemento `dsig:Transforms` es un elemento secundario necesario del elemento `hash`.  El elemento `dsig:Transforms` no tiene atributos.  
  
## dsig:Transform  
 El elemento `dsig:Transform` es un elemento secundario necesario del elemento `dsig:Transforms`.  El elemento `dsig:Transform` presenta los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Algorithm`|Algoritmo que se utiliza para calcular la síntesis de este archivo.  En la actualidad, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## dsig:DigestMethod  
 El elemento `dsig:DigestMethod` es un elemento secundario necesario del elemento `hash`.  El elemento `dsig:DigestMethod` presenta los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Algorithm`|Algoritmo que se utiliza para calcular la síntesis de este archivo.  En la actualidad, el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## dsig:DigestValue  
 El elemento `dsig:DigestValue` es un elemento secundario necesario del elemento `hash`.  El elemento `dsig:DigestValue` no tiene atributos.  Su valor de texto es el valor hash calculado para el archivo especificado.  
  
## Comentarios  
 Este elemento identifica todos los archivos nonassembly que constituyen la aplicación y, en particular, los valores hash para la comprobación del archivo.  Este elemento también puede incluir los datos de aislamiento Componente Modelo de objetos \(COM\) asociados al archivo.  Si un archivo cambia, el archivo de manifiesto de aplicación también debe actualizarse para reflejar el cambio.  
  
## Ejemplo  
 En el siguiente ejemplo de código se ilustran los elementos `file` de un manifiesto para una aplicación implementada mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
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
  
## Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)