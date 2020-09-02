---
title: Cambiar el nombre de la refactorización (C#) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667478"
---
# <a name="rename-refactoring-c"></a>Cambiar el nombre de refactorización (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Rename** es una característica de refactorización en el entorno de desarrollo integrado (IDE) de Visual Studio que proporciona una manera sencilla de cambiar el nombre de los identificadores de símbolos de código como campos, variables locales, métodos, espacios de nombres, propiedades y tipos. **Rename** se puede usar para cambiar los nombres en comentarios y en cadenas, y para cambiar las declaraciones y llamadas de un identificador.

> [!NOTE]
> Al usar el control de código fuente para Visual Studio, obtenga la versión más reciente de los orígenes antes de intentar realizar la refactorización de cambio de nombre.

 La refactorización cambiar nombre está disponible en las siguientes características de Visual Studio:

|Característica|Comportamiento de la refactorización en el IDE|
|-------------|----------------------------------------|
|Editor de código|En el editor de código, la refactorización cambiar nombre está disponible cuando se coloca el cursor en determinados tipos de símbolos de código. Cuando el cursor está en esta posición, puede invocar el comando **cambiar nombre** escribiendo el método abreviado de teclado (Ctrl + r, Ctrl + r) o seleccionando el comando **cambiar nombre** de una etiqueta inteligente, un menú contextual o el menú **refactorizar** .|
|Vista de clases|Al seleccionar un identificador en Vista de clases, el cambio de nombre de la refactorización está disponible en el menú contextual y en el menú **refactorizar** .|
|Examinador de objetos|Al seleccionar un identificador en Examinador de objetos, el cambio de nombre de la refactorización solo está disponible en el menú **refactorizar** .|
|Cuadrícula de propiedades del Diseñador de Windows Forms|En la **cuadrícula de propiedades** del diseñador de Windows Forms, al cambiar el nombre de un control se iniciará una operación de cambio de nombre para ese control. No aparecerá el cuadro de diálogo **cambiar nombre** .|
|Explorador de soluciones|En **Explorador de soluciones**, un comando **cambiar nombre** está disponible en el menú contextual. Si el archivo de código fuente seleccionado contiene una clase cuyo nombre de clase es el mismo que el nombre de archivo, puede usar este comando para cambiar el nombre del archivo de origen simultáneamente y ejecutar la refactorización de cambio de nombre.<br /><br /> Por ejemplo, si crea una aplicación predeterminada basada en Windows y, a continuación, cambia el nombre de Form1.cs a TestForm.cs, el nombre del archivo de código fuente Form1.cs cambiará a TestForm.cs y la clase Form1 y todas las referencias a esa clase cambiarán a TestForm. **Nota:**  El comando **Deshacer** (Ctrl + Z) solo deshará la refactorización de cambio de nombre en el código y no volverá a cambiar el nombre de archivo al nombre original. <br /><br /> Si el archivo de código fuente seleccionado no contiene una clase cuyo nombre es el mismo que el nombre de archivo, el comando **Rename** en **Explorador de soluciones** solo cambiará el nombre del archivo de código fuente y no se ejecutará la refactorización de cambio de nombre.|

## <a name="rename-operations"></a>Cambiar el nombre de las operaciones
 Al ejecutar **Rename**, el motor de refactorización realiza una operación de cambio de nombre específica para cada símbolo de código, tal y como se describe en la tabla siguiente.

|Símbolo de código|Operación de cambio de nombre|
|-----------------|----------------------|
|Campo|Cambia la declaración y los usos del campo al nuevo nombre.|
|Variable local|Cambia la declaración y los usos de la variable al nuevo nombre.|
|Método|Cambia el nombre del método y todas las referencias a ese método por el nuevo nombre. **Nota:**  Al cambiar el nombre de un método de extensión, la operación de cambio de nombre se propaga a todas las instancias del método que están en el ámbito, independientemente de si el método de extensión se está utilizando como un método estático o un método de instancia. Para obtener más información, vea [Métodos de extensión](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|
|Espacio de nombres|Cambia el nombre del espacio de nombres por el nuevo nombre en la declaración, todas las `using` instrucciones y los nombres completos. **Nota:**  Al cambiar el nombre de un espacio de nombres, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] también actualiza la propiedad **espacio de nombres predeterminado** en la página **aplicación** del **Diseñador de proyectos**. Esta propiedad no se puede restablecer seleccionando **Deshacer** en el menú **edición** . Para restablecer el valor predeterminado de la propiedad **espacio de nombres** , debe modificar la propiedad en el diseñador de **proyectos**. Para obtener más información, consulte la página de la [aplicación](../ide/reference/application-page-project-designer-csharp.md).|
|Propiedad|Cambia la declaración y los usos de la propiedad al nuevo nombre.|
|Tipo|Cambia todas las declaraciones y todos los usos del tipo al nuevo nombre, incluidos constructores y destructores. En el caso de los tipos parciales, la operación de cambio de nombre se propagará a todas las partes.|

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

2. Coloque el cursor en `MethodB` , ya sea en la declaración del método o en la llamada al método.

3. En el menú **refactorizar** , seleccione **cambiar nombre**. Aparece el cuadro de diálogo **cambiar nombre** .

     También puede hacer clic con el botón secundario en el cursor, seleccionar **refactorizar** en el menú contextual y, a continuación, hacer clic en **cambiar nombre** para mostrar el cuadro de diálogo **cambiar nombre** .

4. En el campo **nuevo nombre** , escriba `MethodC` .

5. Active la casilla **Buscar en comentarios** .

6. Haga clic en **Aceptar**.

7. En el cuadro de diálogo **vista previa de los cambios** , haga clic en **aplicar**.

#### <a name="to-rename-an-identifier-using-smart-tags"></a>Para cambiar el nombre de un identificador mediante etiquetas inteligentes

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

2. En la declaración de `MethodB` , escriba o retroceso sobre el identificador del método. Aparecerá un mensaje de etiqueta inteligente debajo de este identificador.

    > [!NOTE]
    > Solo se puede invocar la refactorización de cambio de nombre mediante etiquetas inteligentes en la declaración de un identificador.

3. Escriba el método abreviado de teclado MAYÚS + ALT + F10 y, a continuación, presione la flecha abajo para mostrar el menú de etiquetas inteligentes.

     o bien

     Mueva el puntero del mouse sobre la solicitud de etiqueta inteligente para mostrar la etiqueta inteligente. A continuación, mueva el puntero del mouse sobre la etiqueta inteligente y haga clic en la flecha abajo para mostrar el menú de etiquetas inteligentes.

4. Seleccione el elemento de menú **cambiar nombre de ' \<identifer1> ' a ' \<identifier2> '** para invocar la refactorización de cambio de nombre sin una vista previa de los cambios en el código. Todas las referencias a se **\<identifer1>** actualizarán automáticamente a **\<identifier2>** .

     o bien

     Seleccione el elemento de menú **cambiar nombre con vista previa** para invocar la refactorización de cambio de nombre con una vista previa de los cambios en el código. Aparecerá el cuadro de diálogo **vista previa de los cambios** .

## <a name="remarks"></a>Observaciones

## <a name="renaming-implemented-or-overridden-members"></a>Cambiar el nombre de miembros implementados o invalidados
 Al **cambiar el nombre** de un miembro que implementa o invalida o se implementa o invalida por miembros de otros tipos, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] muestra un cuadro de diálogo que indica que la operación de cambio de nombre producirá actualizaciones en cascada. Si hace clic en **continuar**, el motor de refactorización busca y cambia de nombre de forma recursiva todos los miembros de los tipos base y derivado que tienen relaciones implementadas e invalidaciones con el miembro al que se va a cambiar el nombre.

 El ejemplo de código siguiente contiene miembros con relaciones implementaciones e invalidaciones.

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 En el ejemplo anterior, el cambio de `C.Method()` nombre también cambia el nombre `Ibase.Method()` porque `C.Method()` implementa `Ibase.Method()` . A continuación, el motor de refactorización ve de forma recursiva que `Ibase.Method()` es implementado por `Derived.Method()` y cambia de nombre `Derived.Method()` . El motor de refactorización no cambia el nombre `Base.Method()` , ya que no `Derived.Method()` invalida `Base.Method()` . El motor de refactorización se detiene aquí a menos que tenga la opción **cambiar nombre de sobrecargas** activada en el cuadro de diálogo **cambiar nombre** .

 Si se activa **cambiar el nombre de sobrecargas** , el motor de refactorización cambia de nombre `Derived.Method(int i)` porque sobrecarga `Derived.Method()` , `Base.Method(int i)` ya que es reemplazado por `Derived.Method(int i)` y `Base.Method()` porque es una sobrecarga de `Base.Method(int i)` .

> [!NOTE]
> Al cambiar el nombre de un miembro que se ha definido en un ensamblado al que se hace referencia, un cuadro de diálogo explica que el cambio de nombre provocará errores de compilación.

## <a name="renaming-properties-of-anonymous-types"></a>Cambiar el nombre de las propiedades de tipos anónimos
 Al cambiar el nombre de una propiedad en tipos anónimos, la operación de cambio de nombre se propagará a las propiedades de otros tipos anónimos que tengan las mismas propiedades. En los siguientes ejemplos se muestra este comportamiento.

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 En el código anterior, el `ID` cambio de nombre cambiará `ID` en ambas instrucciones porque tienen el mismo tipo anónimo subyacente.

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 En el código anterior, el cambio de `ID` nombre solo cambiará el nombre de una instancia de `ID` porque `companyIDs` y `orderIDs` no tienen las mismas propiedades.

## <a name="see-also"></a>Consulte también
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md) [tipos anónimos](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)