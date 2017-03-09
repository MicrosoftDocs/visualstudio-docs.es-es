---
title: "Cambiar el nombre de refactorizaci&#243;n (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.rename"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactorización [C#], cambio de nombre"
  - "refactorización de cambio de nombre [C#]"
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
caps.handback.revision: 45
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cambiar el nombre de refactorizaci&#243;n (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Cambiar nombre** es una característica de refactorización del entorno integrado de desarrollo \(IDE\) de Visual Studio que proporciona una manera fácil de cambiar el nombre de los identificadores para los símbolos del código, tales como campos, variables locales, métodos, espacios de nombres, propiedades y tipos.  **Cambiar nombre** se puede utilizar para cambiar los nombres en los comentarios y en las cadenas, además de en las declaraciones y las llamadas de un identificador.  
  
> [!NOTE]
>  Cuando utilice control de código fuente para Visual Studio, obtenga siempre la última versión de los archivos de código fuente antes de intentar ejecutar la refactorización de cambio de nombre.  
  
 La operación de refactorización Cambiar nombre está disponible en las características de Visual Studio siguientes:  
  
|Característica|Comportamiento de la refactorización en el IDE|  
|--------------------|----------------------------------------------------|  
|Editor de código|En el editor de código, la operación de refactorización Cambiar nombre está disponible cuando se sitúa el cursor en ciertos tipos de símbolos de código.  Cuando el cursor está en esta posición, puede invocar el comando de **Cambiar nombre** escribiendo el método abreviado de teclado \(CTRL \+ r, CTRL \+ R\), o seleccionando el comando de **Cambiar nombre** de una etiqueta inteligente, de menú contextual, o desde el menú de **Refactorizar** .|  
|Vista de clases|Al seleccionar un identificador en la Vista de clases, la operación de refactorización Cambiar nombre está disponible en el menú contextual y en el menú **Refactorizar**.|  
|Examinador de objetos|Cuando se selecciona un identificador en el Explorador de objetos, la operación de refactorización Cambiar nombre sólo está disponible en el menú **Refactorizar**.|  
|Cuadrícula de propiedades del Diseñador de Windows Forms|En la **Cuadrícula de propiedades** del Diseñador de Windows Forms, cuando se cambia el nombre de un control se inicia una operación Cambiar nombre para ese control.  No aparece el cuadro de diálogo **Cambiar nombre**.|  
|Explorador de soluciones|En el **Explorador de soluciones**, el comando **Cambiar nombre** está disponible en el menú contextual.  Si el archivo de código fuente seleccionado contiene una clase cuyo nombre es el mismo que el del archivo, puede utilizar este comando para, simultáneamente, cambiar el nombre del archivo de código fuente y ejecutar la operación de refactorización Cambiar nombre.<br /><br /> Por ejemplo, si crea una aplicación predeterminada basada en Windows y luego cambia el nombre de Form1.cs por TestForm.cs, entonces el nombre del archivo de código fuente Form1.cs cambiará a TestForm.cs, y la clase Form1 y todas las referencias a ella también recibirán el nuevo nombre TestForm. **Note:**  El comando **Deshacer** \(CTRL\+Z\) únicamente deshará la operación de refactorización Cambiar nombre dentro del código, pero no restablecerá el nombre original del archivo. <br /><br /> Si el archivo de código fuente seleccionado no contiene una clase cuyo nombre sea el mismo que el del archivo, el comando **Cambiar nombre** del **Explorador de soluciones** únicamente cambiará el nombre del archivo de código fuente y no ejecutará la operación de refactorización Cambiar nombre.|  
  
## Operaciones de cambio de nombre  
 Al ejecutar **Cambiar nombre**, el motor de refactorización realiza una operación de cambio de nombre específica para cada símbolo de código, como se describe en la tabla siguiente.  
  
|Símbolo de código|Operación de cambio de nombre|  
|-----------------------|-----------------------------------|  
|Campo|Cambia la declaración y los usos del campo al nuevo nombre.|  
|Variable local|Cambia la declaración y los usos de la variable por el nuevo nombre.|  
|Método|Cambia el nombre del método y todas las referencias a ese método al nuevo nombre. **Note:**  Al cambiar el nombre de un método de extensión, la operación de cambio de nombre se propaga a todas las instancias del método que están dentro del ámbito, sin tener en cuenta si el método de extensión se utiliza como un método estático o un método de instancia.  Para obtener más información, consulte [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).|  
|Espacio de nombres|Cambia el nombre del espacio de nombres al nuevo nombre en la declaración, en todas las instrucciones `using` y en los nombres completos. **Note:**  Al cambiar el nombre de un espacio de nombres, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] actualiza también la propiedad **Default Namespace** en la página **Aplicación** del **Diseñador de proyectos**.  Esta propiedad no se puede restablecer seleccionando **Deshacer** en el menú **Editar**.  Para restablecer el valor de propiedad **Default Namespace**, debe modificar la propiedad en el **Diseñador de proyectos**.  Para obtener más información, vea [Página Aplicación](../ide/reference/application-page-project-designer-csharp.md).|  
|Propiedad.|Cambia la declaración y los usos de la propiedad al nuevo nombre.|  
|Tipo|Cambia todas las declaraciones y todos los usos del tipo por el nuevo nombre, incluso los constructores y destructores.  Para los tipos parciales, la operación Cambiar nombre se propaga a todas las partes.|  
  
#### Para cambiar el nombre de un identificador  
  
1.  Cree una aplicación de consola denominada `RenameIdentifier` y, a continuación, reemplace `Program` por el ejemplo de código siguiente.  
  
    ```c#  
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
  
2.  Coloque el cursor en `MethodB`, en la declaración de método o la llamada al método.  
  
3.  En el menú **Refactorizar**, seleccione **Cambiar nombre**.  Aparece el cuadro de diálogo **Cambiar nombre**.  
  
     O bien, puede hacer clic con el botón secundario en el cursor, señalar **Refactorizar** en el menú contextual y, a continuación, hacer clic en **Cambiar nombre** para mostrar el cuadro de diálogo **Cambiar nombre**.  
  
4.  En el cuadro **Nuevo nombre**, escriba `MethodC`.  
  
5.  Active la casilla **Buscar en los comentarios**.  
  
6.  Haga clic en **Aceptar**.  
  
7.  En el cuadro de diálogo **Obtener vista previa de cambios**, haga clic en **Aplicar**.  
  
#### Para cambiar el nombre de un identificador utilizando las etiquetas inteligentes  
  
1.  Cree una aplicación de consola denominada `RenameIdentifier` y, a continuación, reemplace `Program` por el ejemplo de código siguiente.  
  
    ```c#  
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
  
2.  En la declaración para `MethodB`, escriba o retroceda sobre el identificador de método.  Aparecerá el texto de la etiqueta inteligente debajo de este identificador.  
  
    > [!NOTE]
    >  Sólo puede invocar la operación de refactorización Cambiar nombre utilizando etiquetas inteligentes en la declaración de un identificador.  
  
3.  Presione MAYÚS\+ALT\+F10 y, a continuación, la FLECHA ABAJO para mostrar el menú de etiquetas inteligentes.  
  
     O bien  
  
     Mueva el puntero del mouse sobre el texto de la etiqueta inteligente para mostrarla.  A continuación, mueva el puntero del mouse sobre la etiqueta inteligente y haga clic en FLECHA ABAJO para mostrar el menú de etiquetas inteligentes.  
  
4.  Seleccione la opción de menú **Cambiar nombre de '**\<identificador1\>**' a '**\<identificador2\>**'**, para invocar la refactorización de cambio de nombre sin ver una vista previa de los cambios del código.  Todas las referencias a \<identificador1\> se actualizarán automáticamente a \<identificador2\>.  
  
     O bien  
  
     Seleccione el elemento de menú **Cambiar nombre con vista previa**, para invocar la refactorización de cambio de nombre con una vista previa de los cambios del código.  Aparecerá el cuadro de diálogo **Obtener vista previa de cambios**.  
  
## Comentarios  
  
## Cambiar el nombre de miembros implementados o invalidados  
 Cuando se realiza la operación **Cambiar nombre** sobre un miembro que implementa o invalida, o es implementado o invalidado por, miembros de otros tipos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muestra un cuadro de diálogo en el que se indica que la operación de cambio de nombre producirá actualizaciones en cascada.  Si hace clic en **Continuar**, el motor de refactorización busca y cambia de nombre de forma recursiva todos los miembros en tipos base y derivados que mantengan relaciones de implementación o sustitución con el miembro al que se va a cambiar de nombre.  
  
 El ejemplo de código siguiente contiene miembros con relaciones de implementación o sustitución.  
  
 [!code-cs[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 En el ejemplo anterior, al cambiar el nombre de `C.Method()` se cambia también el nombre de `Ibase.Method()`, ya que `C.Method()` implementa `Ibase.Method()`.  A continuación, el motor de refactorización determina de forma recursiva que `Ibase.Method()` está implementado por `Derived.Method()` y cambia el nombre de `Derived.Method()`.  El motor de refactorización no cambia el nombre de `Base.Method()`, porque `Derived.Method()` no reemplaza `Base.Method()`.  El motor de refactorización se detiene aquí a menos que haya activado **Cambiar el nombre de las sobrecargas** en el cuadro de diálogo **Cambiar nombre**.  
  
 Si **Cambiar el nombre de las sobrecargas** está activado, el motor de refactorización cambia el nombre de `Derived.Method(int i)` porque sobrecarga `Derived.Method()`, de `Base.Method(int i)` porque es reemplazado por `Derived.Method(int i)` y de `Base.Method()` porque es una sobrecarga de `Base.Method(int i)`.  
  
> [!NOTE]
>  Al cambiar el nombre de un miembro que se ha definido en un ensamblado al que se hace referencia, aparece un cuadro de diálogo en el que se explica que ese cambio producirá errores de compilación.  
  
## Cambiar el nombre a propiedades de tipos anónimos  
 Al cambiar el nombre a una propiedad en tipos anónimos, la operación de cambio de nombre se propagará a las propiedades de otros tipos anónimos que tengan las mismas propiedades.  En el siguiente ejemplo, se muestra este comportamiento:  
  
```c#  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 En el código anterior, al cambiar el nombre de `ID`, se cambiará `ID` en ambas instrucciones, ya que poseen el mismo tipo anónimo subyacente.  
  
```c#  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 En el código anterior, al cambiar el nombre a `ID`, cambiará sólo el nombre de una instancia de `ID`, ya que `companyIDs` y `orderIDs` no tienen las mismas propiedades.  
  
## Vea también  
 [Refactorización \(C\#\)](../csharp-ide/refactoring-csharp.md)   
 [Tipos anónimos](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)