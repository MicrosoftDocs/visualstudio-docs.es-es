---
title: "Text Template Utility Methods | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, utility methods"
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 50
caps.handback.revision: 50
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Text Template Utility Methods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Existen varios métodos que siempre están disponibles al escribir código en una plantilla de texto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Estos métodos se definen en <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  También puede utilizar otros métodos y servicios proporcionados por el entorno host en una plantilla de texto normal \(sin preprocesamiento\).  Por ejemplo, puede resolver rutas de acceso de archivo, registrar errores y obtener servicios proporcionados por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y cualquier paquete cargado.  Para obtener más información, vea [Accessing Visual Studio from a Text Template](http://msdn.microsoft.com/es-es/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## Métodos de escritura  
 Puede utilizar los métodos `Write()` y `WriteLine()` para anexar el texto dentro de un bloque de código estándar, en lugar de utilizar un bloque de código de expresiones.  Los dos bloques de código siguientes tienen una funcionalidad equivalente.  
  
##### Bloque de código con un bloque de expresiones  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### Bloque de código que usa WriteLine\(\)  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Puede que le resulte útil usa uno de estos métodos de utilidad en lugar de un bloque de expresiones dentro de un bloque de código largo con estructuras de control anidadas.  
  
 Los métodos `Write()` y `WriteLine()` tienen dos sobrecargas, una que toma un parámetro de cadena único y otra que toma una cadena de formato compuesto más una matriz de objetos para incluir en la cadena \(como el método `Console.WriteLine()`\).  Los dos usos siguientes de `WriteLine()` tienen una funcionalidad equivalente:  
  
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
  
## Métodos de sangría  
 Puede utilizar métodos de sangría para dar formato al resultado de la plantilla de texto.  La clase <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> tiene una propiedad de cadena `CurrentIndent` que muestra la sangría actual de la plantilla de texto y un campo `indentLengths` que es una lista de las sangrías que se han agregado.  Puede agregar una sangría con el método `PushIndent()`  y restar una sangría con el método `PopIndent()`.  Si desea quitar todas las sangrías, use el método `ClearIndent()`.  En el bloque de código siguiente se muestra el uso de estos métodos:  
  
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
  
 Este bloque de código genera el resultado siguiente:  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## Métodos de advertencia y error  
 Puede utilizar métodos de utilidad de advertencia y error para agregar mensajes a la Lista de errores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Por ejemplo, el siguiente código agregará un mensaje de error a la lista de errores.  
  
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
  
## Obtener acceso al host y al proveedor de servicio  
 La propiedad `this.Host` puede proporcionar acceso a las propiedades que expone el host que ejecuta la plantilla.  Para utilizar `this.Host`, debe establecer el atributo `hostspecific` de la directiva `<@template#>`:  
  
 `<#@template ...  hostspecific="true" #>`  
  
 El tipo de `this.Host` depende del tipo de host donde se ejecuta la plantilla.  En una plantilla que se ejecuta en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede convertir `this.Host` en `IServiceProvider` para obtener acceso a servicios como el IDE.  Por ejemplo:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## Usar un conjunto diferente de métodos de utilidad  
 Como parte del proceso de generación de texto, el archivo de plantilla se transforma en una clase, que siempre tiene el nombre `GeneratedTextTransformation` y hereda de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  Si desea utilizar un conjunto diferente de métodos en su lugar, puede escribir su propia clase y especificarla en la directiva de plantilla.  Esta clase debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Utilice la directiva `assembly` para hacer referencia al ensamblado donde se puede encontrar la clase compilada.