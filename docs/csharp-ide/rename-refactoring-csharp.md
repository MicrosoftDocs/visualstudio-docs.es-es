---
redirect_url: /visualstudio/csharp-ide/refactoring/rename
title: "Cambiar el nombre de refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 42c5f99b3bf5ba95bc279cd5e117745ccc8e02c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="rename-refactoring-c"></a>Cambiar el nombre de refactorización (C#)
**Cambiar el nombre de** es una característica de refactorización en el entorno de desarrollo integrado (IDE) de Visual Studio que proporciona una manera sencilla de cambiar el nombre de los identificadores de símbolos de código, como campos, variables locales, métodos, espacios de nombres, propiedades y tipos. **Cambiar el nombre de** puede utilizarse para cambiar los nombres en los comentarios y en las cadenas y cambiar las declaraciones y las llamadas de un identificador.  
  
> [!NOTE]
>  Cuando se usa el Control de código fuente para Visual Studio, obtener la versión más reciente de orígenes antes de intentar realizar la operación de refactorización.  
  
 La operación de refactorización está disponible en las siguientes características de Visual Studio:  
  
|Característica|Comportamiento de la refactorización en el IDE|  
|-------------|----------------------------------------|  
|Editor de código|En el Editor de código, la operación de refactorización está disponible cuando se sitúe el cursor en ciertos tipos de símbolos de código. Cuando el cursor está en esta posición, puede invocar la **cambiar el nombre de** comando escribiendo el método abreviado de teclado (Ctrl + R, Ctrl + R) o seleccionando el **cambiar el nombre de** comando de acciones rápidas, el menú contextual, o **Refactorizar** menú.|  
|Vista de clases|Cuando se selecciona un identificador en la vista de clases, la operación de refactorización está disponible en el menú contextual y **refactorizar** menú.|  
|Examinador de objetos|Cuando se selecciona un identificador en el Examinador de objetos, la operación de refactorización solo está disponible en la **refactorizar** menú.|  
|Cuadrícula de propiedades del Diseñador de Windows Forms|En el **cuadrícula de propiedades** del Diseñador de Windows Forms, cambiar el nombre de un control se iniciará una operación de cambio de nombre de ese control. El **cambiar el nombre de** no aparecerá el cuadro de diálogo.|  
|Explorador de soluciones|En **el Explorador de soluciones**, **cambiar el nombre de** comando está disponible en el menú contextual. Si el archivo de código fuente seleccionado contiene una clase cuyo nombre de clase es el mismo que el nombre de archivo, puede utilizar este comando para cambiar el nombre de archivo de código fuente y ejecutar la operación de refactorización simultáneamente.<br /><br /> Por ejemplo, si crea una aplicación de Windows de forma predeterminada y, a continuación, cambiar el nombre de Form1.cs por TestForm.cs, el nombre de archivo de código fuente Form1.cs cambiará a TestForm.cs y la clase Form1 y todas las referencias a que se puede cambiar el nombre de clase TestForm. **Nota:** el **deshacer** comando (CTRL+Z) sólo deshacer la operación de refactorización en el código y le no volver a cambiar el nombre de archivo al nombre original. <br /><br /> Si el archivo de código fuente seleccionado no contiene una clase cuyo nombre es el mismo que el nombre de archivo, el **cambiar el nombre de** comando **el Explorador de soluciones** sólo se cambiará el nombre del archivo de código fuente y no se ejecutará el cambio de nombre la refactorización.|  
  
## <a name="rename-operations"></a>Cambiar el nombre de las operaciones  
 Cuando se ejecuta **cambiar el nombre de**, el motor de refactorización realiza un determinado de operación de cambio de nombre para cada símbolo de código, tal como se describe en la tabla siguiente.  
  
|Símbolo de código|Cambiar el nombre de operación|  
|-----------------|----------------------|  
|Campo|Cambia la declaración y los usos del campo por el nuevo nombre.|  
|variable local|Cambia la declaración y los usos de la variable por el nuevo nombre.|  
|Método|Cambia el nombre del método y todas las referencias a ese método para el nuevo nombre. **Nota:** cuando cambia el nombre de un método de extensión, la operación de cambio de nombre se propagará a todas las instancias del método que se encuentran en el ámbito, con independencia de si se está utilizando el método de extensión como un método estático o un método de instancia. Para más información, vea [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).|  
|Espacio de nombres|Cambia el nombre del espacio de nombres para el nuevo nombre en la declaración, todas las `using` instrucciones y nombres completos. **Nota:** al cambiar el nombre de un espacio de nombres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] también actualiza el **Default Namespace** propiedad en el **aplicación** página de la **Diseñador de proyectos**. Esta propiedad no se puede restablecer seleccionando **deshacer** desde el **editar** menú. Para restablecer la **Default Namespace** valor de propiedad, debe modificar la propiedad en el **Diseñador de proyectos**. Para obtener más información, consulte [página de la aplicación](../ide/reference/application-page-project-designer-csharp.md).|  
|Property|Cambia la declaración y los usos de la propiedad para el nuevo nombre.|  
|Tipo|Cambia todas las declaraciones y todos los usos del tipo para el nuevo nombre, incluidos los constructores y destructores. Para los tipos parciales, la operación de cambio de nombre se propagará a todas las partes.|  
  
#### <a name="to-rename-an-identifier"></a>Para cambiar el nombre de un identificador  
  
1.  Cree una aplicación de consola denominada `RenameIdentifier` y, a continuación, reemplace `Program` por el siguiente código de ejemplo.  
  
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
  
2.  Coloque el cursor en `MethodB`, en la declaración del método o la llamada al método.  
  
3.  Desde el **refactorizar** menú, seleccione **cambiar el nombre de**. El **cambiar el nombre de** aparece el cuadro de diálogo.  
  
     También puede hacer clic el cursor, seleccione **refactorizar** en el menú contextual y, a continuación, haga clic en **cambiar el nombre de** para mostrar la **cambiar el nombre de** cuadro de diálogo.  
  
4.  En el **nuevo nombre** , escriba `MethodC`.  
  
5.  Seleccione el **buscar en los comentarios** casilla de verificación.  
  
6.  Haga clic en **Aceptar**.  
  
7.  En el **vista previa de cambios** cuadro de diálogo, haga clic en **aplicar**.  
  
#### <a name="to-rename-an-identifier-using-quick-actions"></a>Para cambiar el nombre de un identificador con acciones rápidas  
  
1.  Cree una aplicación de consola denominada `RenameIdentifier` y, a continuación, reemplace `Program` por el siguiente código de ejemplo.  
  
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
  
2.  En la declaración de `MethodB`, escriba o retroceda sobre el identificador de método. Aparecerá una bombilla acciones rápidas en el margen.  
  
    > [!NOTE]
    >  Solo se puede invocar la operación de refactorización con acciones rápidas en la declaración de un identificador.  
  
3.  Escriba el método abreviado de teclado **Alt + Mayús + F10** para mostrar el menú de acciones rápidas.  
  
     O bien  
  
     Haga clic en el triángulo negro situado junto a la bombilla para mostrar el menú de acciones rápidas.  
  
4.  Seleccione el **cambiar el nombre '\<identifer1 >' a '\<identificador2 >'** elemento de menú para invocar la operación de refactorización. Todas las referencias a  **\<identifer1 >** se actualizarán automáticamente a  **\<identificador2 >**.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="renaming-implemented-or-overridden-members"></a>Cambiar el nombre de miembros implementados o invalidados  
 Cuando se **cambiar el nombre de** un miembro que implementa/invalidaciones o está implementado o invalidado por miembros de otros tipos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muestra un cuadro de diálogo que indica la operación de cambio de nombre hará que las actualizaciones en cascada. Si hace clic en **continuar**, la refactorización de forma recursiva motor busca y cambia el nombre de todos los miembros de la base y los tipos derivados que tienen implementa/reemplazos relaciones con el miembro que se va a cambiar el nombre.  
  
 El ejemplo de código siguiente contiene a miembros con relaciones de implementación o sustitución.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 En el ejemplo anterior, el cambio de nombre `C.Method()` también cambia el nombre `Ibase.Method()` porque `C.Method()` implementa `Ibase.Method()`. A continuación, el motor de refactorización de forma recursiva ve que `Ibase.Method()` se implementa mediante `Derived.Method()` y cambia el nombre `Derived.Method()`. El motor de refactorización no cambie el nombre `Base.Method()`, porque `Derived.Method()` no invalida `Base.Method()`. El motor de refactorización se detiene ahí a menos que tenga **cambiar el nombre de las sobrecargas** protegió el **cambiar el nombre de** cuadro de diálogo.  
  
 Si **cambiar el nombre de las sobrecargas** se activa, el motor de refactorización cambia el nombre `Derived.Method(int i)` porque sobrecarga `Derived.Method()`, `Base.Method(int i)` porque es reemplazado por `Derived.Method(int i)`, y `Base.Method()` porque es una sobrecarga de `Base.Method(int i)`.  
  
> [!NOTE]
>  Al cambiar el nombre de un miembro que se definió en un ensamblado de referencia, un cuadro de diálogo explica ese cambio producirá errores de compilación.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Cambiar el nombre de propiedades de tipos anónimos  
 Al cambiar el nombre de una propiedad en tipos anónimos, la operación de cambio de nombre se propagará a las propiedades de otros tipos anónimos que tienen las mismas propiedades. Los ejemplos siguientes muestran este comportamiento.  
  
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
  
 En el código anterior, el cambio de nombre `ID` sólo se cambiará el nombre de una instancia de `ID` porque `companyIDs` y `orderIDs` no tiene las mismas propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](refactoring-csharp.md)   
 [Tipos anónimos](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)