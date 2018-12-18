---
title: Métodos de utilidad de plantilla de texto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4a9c5a0b4b6c85a301c5d3a0e12ad3687f54aeb0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186308"
---
# <a name="text-template-utility-methods"></a>Métodos de utilidad de las plantillas de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Existen varios métodos que siempre están disponibles al escribir código en un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plantilla de texto. Estos métodos se definen en <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  También puede usar otros métodos y los servicios proporcionados por el entorno de host en una plantilla de texto (preprocesada no) normal. Por ejemplo, puede resolver las rutas de acceso de archivo, registrar errores y obtener servicios proporcionados por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y cualquier carga de paquetes.  Para obtener más información, consulte [acceso a Visual Studio desde una plantilla de texto](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Escribir métodos  
 Puede usar el `Write()` y `WriteLine()` métodos anexar texto dentro de un bloque de código estándar, en lugar de usar un bloque de código de expresiones. Los siguientes bloques de código de dos son funcionalmente equivalentes.  
  
##### <a name="code-block-with-an-expression-block"></a>Bloque de código con un bloque de expresiones  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>Bloque de código mediante WriteLine()  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Le resultará útil usar uno de estos métodos de utilidad en lugar de un bloque de expresiones dentro de un bloque de código largo con estructuras de control anidadas.  
  
 El `Write()` y `WriteLine()` métodos tienen dos sobrecargas, una que toma un parámetro de cadena único y otra que toma una cadena de formato compuesto más una matriz de objetos que se va a incluir en la cadena (como el `Console.WriteLine()` método). Los siguientes dos usos de `WriteLine()` son funcionalmente equivalentes:  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## <a name="indentation-methods"></a>Métodos de sangría  
 Puede utilizar métodos de sangría para dar formato al resultado de la plantilla de texto. El <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> clase tiene un `CurrentIndent` propiedad de cadena que se muestra la sangría actual en la plantilla de texto y un `indentLengths` campo, es decir, una lista de las sangrías que se han agregado. Puede agregar una sangría con el `PushIndent()` método y restar una sangría con el `PopIndent()` método. Si desea quitar todas las sangrías, utilice el `ClearIndent()` método. El bloque de código siguiente muestra el uso de estos métodos:  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 Este bloque de código genera el siguiente resultado:  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>Métodos de advertencia y error  
 Puede usar los métodos de utilidad de advertencia y error para agregar mensajes a la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lista de errores. Por ejemplo, el código siguiente agregará un mensaje de error en la lista de errores.  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## <a name="access-to-host-and-service-provider"></a>Acceso al Host y el proveedor de servicios  
 La propiedad `this.Host` puede proporcionar acceso a las propiedades expuestas por el host que se está ejecutando la plantilla. Para usar `this.Host`, debe establecer `hostspecific` atributo el `<@template#>` directiva:  
  
 `<#@template ... hostspecific="true" #>`  
  
 El tipo de `this.Host` depende del tipo de host en el que se ejecuta la plantilla. En una plantilla que se está ejecutando en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede convertir `this.Host` a `IServiceProvider` para obtener acceso a servicios como el IDE. Por ejemplo:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>Con un conjunto diferente de métodos de utilidad  
 Como parte del proceso de generación de texto, el archivo de plantilla se transforma en una clase, que siempre se denomina `GeneratedTextTransformation`y hereda de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Si desea usar otro conjunto de métodos en su lugar, puede escribir su propia clase y especificarla en la directiva de plantilla. La clase debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Use el `assembly` directiva para hacer referencia al ensamblado donde se puede encontrar la clase compilada.



