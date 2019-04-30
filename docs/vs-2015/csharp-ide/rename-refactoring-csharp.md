---
title: Cambiar el nombre de refactorización (C#) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 971ca4e94f28016335483a03f4b0121de587f00d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439955"
---
# <a name="rename-refactoring-c"></a>Cambiar el nombre de refactorización (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Cambiar el nombre** es una característica de refactorización en el entorno de desarrollo integrado (IDE) de Visual Studio que proporciona una manera fácil de cambiar el nombre de los identificadores de símbolos de código, como campos, variables locales, métodos, espacios de nombres, propiedades y tipos. **Cambiar el nombre de** puede utilizarse para cambiar los nombres en los comentarios y en las cadenas y cambiar las declaraciones y las llamadas de un identificador.  
  
> [!NOTE]
> Cuando se usa el Control de código fuente para Visual Studio, obtenga la versión más reciente de los orígenes antes de intentar realizar la operación de refactorización.  
  
 La operación de refactorización está disponible en las siguientes características de Visual Studio:  
  
|Característica|Comportamiento de la refactorización en el IDE|  
|-------------|----------------------------------------|  
|Editor de código|En el Editor de código, la operación de refactorización está disponible cuando se coloca el cursor en ciertos tipos de símbolos de código. Cuando el cursor está en esta posición, puede invocar el **cambiar el nombre de** comando escribiendo el método abreviado de teclado (CTRL + R, CTRL + R), o bien seleccionando la **cambiar el nombre de** comando en una etiqueta inteligente, el menú contextual o el  **Refactorizar** menú.|  
|Vista de clases|Cuando se selecciona un identificador en la vista de clases, la operación de refactorización está disponible en el menú contextual y **refactorizar** menú.|  
|Examinador de objetos|Cuando se selecciona un identificador en el Examinador de objetos, la operación de refactorización solo está disponible desde el **refactorizar** menú.|  
|Cuadrícula de propiedades del Diseñador de Windows Forms|En el **cuadrícula de propiedades** del Diseñador de Windows Forms, cambiar el nombre de un control iniciará una operación de cambio de nombre de ese control. El **cambiar el nombre de** no aparecerá el cuadro de diálogo.|  
|Explorador de soluciones|En **el Explorador de soluciones**, un **cambiar el nombre de** comando está disponible en el menú contextual. Si el archivo de código fuente seleccionado contiene una clase cuyo nombre es el mismo que el nombre de archivo, puede usar este comando para cambiar el nombre de archivo de código fuente y ejecutar la operación de refactorización simultáneamente.<br /><br /> Por ejemplo, si crea una aplicación de Windows de forma predeterminada y, a continuación, cambie el nombre Form1.cs a TestForm.cs, el nombre de archivo de código fuente Form1.cs cambiará a TestForm.cs y la clase Form1 y todas las referencias a que se cambiará la clase TestForm. **Nota:**  El **deshacer** solo (CTRL + Z) del comando Deshacer la operación de refactorización en el código y le no los cambie el nombre de archivo nuevo al nombre original. <br /><br /> Si el archivo de código fuente seleccionado no contiene una clase cuyo nombre es el mismo que el nombre de archivo, el **cambiar el nombre de** comando **el Explorador de soluciones** sólo se cambiará el nombre del archivo de código fuente y no se ejecutará el cambio de nombre la refactorización.|  
  
## <a name="rename-operations"></a>Cambiar el nombre de las operaciones  
 Cuando se ejecuta **cambiar el nombre**, el motor de refactorización realiza una determinada operación de cambio de nombre para cada símbolo de código, como se describe en la tabla siguiente.  
  
|Símbolo de código|Cambiar el nombre de operación|  
|-----------------|----------------------|  
|Campo|Cambia la declaración y los usos del campo por el nombre nuevo.|  
|variable local|Cambia la declaración y los usos de la variable en el nuevo nombre.|  
|Método|Cambia el nombre del método y todas las referencias a ese método para el nuevo nombre. **Nota:**  Al cambiar el nombre de un método de extensión, la operación de cambio se propaga a todas las instancias del método que están en el ámbito, independientemente de si se utiliza el método de extensión como un método estático o un método de instancia. Para obtener más información, vea [Métodos de extensión](http://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|  
|Espacio de nombres|Cambia el nombre del espacio de nombres para el nuevo nombre en la declaración, todos los `using` instrucciones y nombres completos. **Nota:**  Al cambiar el nombre de un espacio de nombres [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] también actualiza el **Default Namespace** propiedad en el **aplicación** página de la **Diseñador de proyectos**. Esta propiedad no se puede restablecer seleccionando **deshacer** desde el **editar** menú. Para restablecer la **Default Namespace** valor de propiedad, debe modificar la propiedad en el **Diseñador de proyectos**. Para obtener más información, consulte [página aplicación](../ide/reference/application-page-project-designer-csharp.md).|  
|Propiedad|Cambia la declaración y los usos de la propiedad para el nuevo nombre.|  
|Tipo|Cambia todas las declaraciones y todos los usos del tipo para el nuevo nombre, incluidos constructores y destructores. Para los tipos parciales, la operación de cambio se propagará a todas las partes.|  
  
#### <a name="to-rename-an-identifier"></a>Para cambiar el nombre de un identificador  
  
1. Cree una aplicación de consola denominada `RenameIdentifier` y, a continuación, reemplace `Program` por el siguiente código de ejemplo.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2. Coloque el cursor en `MethodB`, ya sea en la declaración de método o la llamada al método.  
  
3. Desde el **refactorizar** menú, seleccione **cambiar el nombre**. El **cambiar el nombre** aparece el cuadro de diálogo.  
  
     También puede haga clic en el cursor, apuntar a **refactorizar** en el menú contextual y, a continuación, haga clic en **cambiar el nombre de** para mostrar el **cambiar el nombre de** cuadro de diálogo.  
  
4. En el **nuevo nombre** , escriba `MethodC`.  
  
5. Seleccione el **buscar en los comentarios** casilla de verificación.  
  
6. Haga clic en **Aceptar**.  
  
7. En el **vista previa de cambios** cuadro de diálogo, haga clic en **aplicar**.  
  
#### <a name="to-rename-an-identifier-using-smart-tags"></a>Para cambiar el nombre de un identificador de etiquetas inteligentes  
  
1. Cree una aplicación de consola denominada `RenameIdentifier` y, a continuación, reemplace `Program` por el siguiente código de ejemplo.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2. En la declaración de `MethodB`, escriba o borrarlo el identificador de método. Aparecerá un mensaje de etiqueta inteligente por debajo de este identificador.  
  
    > [!NOTE]
    > Sólo puede invocar la operación de refactorización con las etiquetas inteligentes en la declaración de un identificador.  
  
3. Escriba el método abreviado de teclado MAYÚS + ALT + F10 y, a continuación, presione la flecha abajo para mostrar el menú de etiquetas inteligentes.  
  
     -o bien-  
  
     Mueva el puntero del mouse sobre el símbolo del sistema de etiqueta inteligente para mostrar la etiqueta inteligente. A continuación, mueva el puntero del mouse sobre la etiqueta inteligente y haga clic en la flecha hacia abajo para mostrar el menú de etiquetas inteligentes.  
  
4. Seleccione el **cambiar el nombre '\<identifer1 >' a '\<identificador2 >'** elemento de menú para invocar la operación de refactorización sin una vista previa de los cambios en el código. Todas las referencias a  **\<identifer1 >** se actualizarán automáticamente a  **\<identificador2 >**.  
  
     -o bien-  
  
     Seleccione el **cambiar el nombre con la versión preliminar** elemento de menú para invocar la operación de refactorización con una vista previa de los cambios en el código. El **vista previa de cambios** aparecerá el cuadro de diálogo.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="renaming-implemented-or-overridden-members"></a>Los miembros invalidados o el cambio de nombre implementado  
 Cuando se **cambiar el nombre de** un miembro que implementa o invalida o está implementado o invalidado por miembros de otros tipos, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] muestra un cuadro de diálogo que dice que la operación de cambio de nombre hará que las actualizaciones en cascada. Si hace clic en **continuar**, el motor de forma recursiva refactorización busca y cambia el nombre de todos los miembros de la base y tipos derivados que tienen implementa/invalidaciones relaciones con el que se va a cambiar el nombre de miembro.  
  
 El siguiente ejemplo de código contiene a miembros con relaciones de implementación o sustitución.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 En el ejemplo anterior, el cambio de nombre `C.Method()` también cambia el nombre `Ibase.Method()` porque `C.Method()` implementa `Ibase.Method()`. A continuación, el motor de refactorización de forma recursiva ve que `Ibase.Method()` se implementa mediante `Derived.Method()` y cambia el nombre `Derived.Method()`. El motor de refactorización no cambie el nombre `Base.Method()`, porque `Derived.Method()` no invalida `Base.Method()`. El motor de refactorización se detiene ahí a menos que tenga **cambiar el nombre de las sobrecargas** protegió el **cambiar el nombre de** cuadro de diálogo.  
  
 Si **cambiar el nombre de las sobrecargas** está activada, el motor de refactorización cambia el nombre `Derived.Method(int i)` porque sobrecarga `Derived.Method()`, `Base.Method(int i)` porque se haya reemplazado por `Derived.Method(int i)`, y `Base.Method()` porque es una sobrecarga de `Base.Method(int i)`.  
  
> [!NOTE]
> Al cambiar el nombre de un miembro que se definió en un ensamblado de referencia, un cuadro de diálogo explica ese cambio producirá errores de compilación.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Cambiar el nombre de las propiedades de tipos anónimos  
 Al cambiar el nombre de una propiedad en tipos anónimos, la operación de cambio se propagará a propiedades de otros tipos anónimos que tienen las mismas propiedades. Los ejemplos siguientes muestran este comportamiento.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 En el código anterior, el cambio de nombre `ID` cambiará `ID` en ambas instrucciones porque tienen el mismo tipo anónimo subyacente.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 En el código anterior, el cambio de nombre `ID` sólo se cambiará el nombre de una instancia de `ID` porque `companyIDs` y `orderIDs` no tienen las mismas propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)   
 [Tipos anónimos](http://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)