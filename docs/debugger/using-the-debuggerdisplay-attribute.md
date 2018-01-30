---
title: Usar el atributo DebuggerDisplay | Documentos de Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 11770efcc517b9ec713656f540d75b0a2c412ae7
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="using-the-debuggerdisplay-attribute"></a>Usar el atributo DebuggerDisplay
El [DebuggerDisplayAttribute (clase)](/dotnet/api/system.diagnostics.debuggerdisplayattribute) controla cómo se muestra un objeto, propiedad o campo en las ventanas de variables del depurador. Este atributo se puede aplicar a tipos, delegados, propiedades, campos y ensamblados.  
  
 El atributo `DebuggerDisplay` tiene un argumento único, que es una cadena que se va a mostrar en la columna de valor de las instancias del tipo. Esta cadena puede contener llaves (`{` y `}`). El texto encerrado entre llaves se evalúa como un campo, una propiedad o un método.  
  
 Si una clase tiene un método `ToString()` invalidado, el depurador usa el método invalidado en lugar del atributo `{<typeName>}`predeterminado. Por lo tanto, si invalidó el método `ToString()` , el depurador usa el método invalidado en lugar del atributo`{<typeName>}`predeterminado, y no tiene que usar `DebuggerDisplay`. Si usa ambos, el atributo `DebuggerDisplay` tiene prioridad sobre el método `ToString()` invalidado.  
  
 La evaluación de esta llamada implícita a `ToString()` por parte del depurador depende de un valor de configuración del usuario del cuadro de diálogo **Herramientas / Opciones/ Depuración** . Visual Basic no implementa esta evaluación implícita de `ToString()` .  
  
> [!IMPORTANT]
>  Si la casilla **Mostrar la estructura de los objetos en ventanas de variables** está seleccionada en el cuadro de diálogo **Herramientas / Opciones/ Depuración** , se omite el atributo `DebuggerDisplay` .  
  
 En la tabla siguiente se muestran algunos posibles usos del atributo `DebuggerDisplay` y resultados de ejemplo.  
  
|Atributo|Resultado que aparece en la columna de valor|  
|---------------|------------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Se utiliza en un tipo con campos `x` y `y`.|`x = 5 y = 18`|  
|La sintaxis del parámetro`[DebuggerDisplay("String value is {getString()}")]`puede variar según el lenguaje. Por consiguiente, utilícela con cuidado.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` también puede aceptar parámetros con nombre.  
  
|Parámetros|Propósito|  
|----------------|-------------|  
|`Name`, `Type`|Estos parámetros afectan a las columnas **Nombre** y **Tipo** de las ventanas de variables. (Se pueden establecer en cadenas mediante la misma sintaxis que el constructor). El uso excesivo o incorrecto de estos parámetros puede generar resultados confusos.|  
|`Target`, `TargetTypeName`|Especifica el tipo de destino cuando se utiliza el atributo en el nivel de ensamblado.|  
  
 El archivo autoexp.cs usa el atributo DebuggerDisplay en el nivel de ensamblado. El archivo autoexp.cs determina las expansiones predeterminadas que usa Visual Studio para los objetos .NET. Puede examinar el archivo autoexp.cs para ver ejemplos de cómo usar el atributo DebuggerDisplay, o puede modificar y compilar el archivo autoexp.cs para cambiar las expansiones predeterminadas. Asegúrese de hacer un copia de seguridad del archivo autoexp.cs antes de modificarlo.  
  
 Para compilar autoexp.cs, abra un Símbolo del sistema para desarrolladores para VS2015 y ejecute los siguientes comandos.  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 Los cambios de autoexp.dll se recogerán en la siguiente sesión de depuración.  
  
## <a name="using-expressions-in-debuggerdisplay"></a>Utilizar expresiones en DebuggerDisplay  
 Aunque puede utilizar una expresión general entre llaves en un atributo DebuggerDisplay, esta práctica no es recomendable.  
  
 Una expresión general en DebuggerDisplay tiene acceso implícito al puntero `this` solo para la instancia actual del tipo de destino. La expresión no tiene acceso a los alias, variables locales ni punteros. Si la expresión hace referencia a propiedades, no se procesan los atributos en dichas propiedades. Por ejemplo, el código de C# `[DebuggerDisplay("Object {count - 2}")]` mostraría `Object 6` si el campo `count` fuera 8.  
  
 El uso de expresiones en DebuggerDisplay puede causar los siguientes problemas:  
  
-   La evaluación de expresiones es la operación más costosa del depurador y la expresión se evalúa cada vez que se muestra. Esto puede causar problemas de rendimiento al recorrer el código. Por ejemplo, una expresión compleja que se usa para mostrar los valores de una colección o lista puede ser muy lenta si incluye un número elevado de elementos.  
  
-   Las expresiones las evalúa el evaluador de expresiones del lenguaje del marco de pila actual, no el evaluador del lenguaje en el que se escribió la expresión. Esto puede provocar resultados imprevisibles cuando los lenguajes son distintos.  
  
-   La evaluación de una expresión puede cambiar el estado de la aplicación. Por ejemplo, una expresión que establece el valor de una propiedad muta el valor de la propiedad en el código en ejecución.  
  
 Una forma de reducir los posibles problemas de la evaluación de expresiones es crear una propiedad privada que realice la operación y devuelva una cadena. A continuación, el atributo DebuggerDisplay puede mostrar el valor de dicha propiedad privada. En el ejemplo siguiente se implementa este patrón:  
  
```csharp  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
public sealed class MyClass   
{      
    public int count { get; set; }      
    public bool flag { get; set; }      
    private string DebuggerDisplay  
   {         
        get  
        {  
             return string.Format("Object {0}", count - 2);  
        }      
    }  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo utilizar `DebuggerDisplay`, junto con `DebuggerBrowseable` y `DebuggerTypeProxy`. Cuando se ve en una ventana de variables del depurador, como la ventana **Inspección** , genera una expansión similar a la siguiente:  
  
|**Name**|**Valor**|**Type**|  
|--------------|---------------|--------------|  
|Key|"three"|object {string}|  
|Valor|3|object {int}|  
  
```csharp  
[DebuggerDisplay("{value}", Name = "{key}")]  
internal class KeyValuePairs  
{  
    private IDictionary dictionary;  
    private object key;  
    private object value;  
    public KeyValuePairs(IDictionary dictionary, object key, object value)  
    {  
        this.value = value;  
        this.key = key;  
        this.dictionary = dictionary;  
    }  
  
    public object Key  
    {  
        get { return key; }  
        set  
        {  
            object tempValue = dictionary[key];  
            dictionary.Remove(key);  
            key = value;  
            dictionary.Add(key, tempValue);  
        }  
    }  
  
    public object Value  
    {  
        get { return this.value; }  
        set  
        {  
            this.value = value;  
            dictionary[key] = this.value;  
        }  
    }  
}  
  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable  
{  
    public Hashtable hashtable;  
  
    public MyHashtable()  
    {  
        hashtable = new Hashtable();    
    }
    
    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
    private class HashtableDebugView  
    {  
        private MyHashtable myhashtable;  
        public HashtableDebugView(MyHashtable myhashtable)  
        {  
            this.myhashtable = myhashtable;  
        }  
  
        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]  
        public KeyValuePairs[] Keys  
        {  
            get  
            {  
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];  
  
                int i = 0;  
                foreach (object key in myhashtable.hashtable.Keys)  
                {  
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);  
                    i++;  
                }  
                return keys;  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Utilizar el atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Crear vistas personalizadas de los objetos administrados](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Especificadores de formato en C#](../debugger/format-specifiers-in-csharp.md)   
 [Mejorar la depuración con los atributos de visualización del depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
