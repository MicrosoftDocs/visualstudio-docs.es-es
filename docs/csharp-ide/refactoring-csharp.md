---
title: "Refactorizaci&#243;n (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.preview"
  - "vs.csharp.refactoring.issues"
  - "vs.csharp.refactoring.buildwarning"
  - "VS.PreviewChanges"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactorización [C#]"
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refactorizaci&#243;n (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La refactorización es el proceso que consiste en mejorar el código una vez escrito cambiando su estructura interna sin modificar su comportamiento externo.  
  
 Visual C\# proporciona los siguientes comandos de refactorización en el menú **Refactorización**:  
  
-   [Extraer método \(Refactorización, C\#\)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Cambiar el nombre de refactorización \(C\#\)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Encapsular campo \(Refactorización, C\#\)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Extraer interfaz \(Refactorización, C\#\)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Quitar parámetros \(Refactorización, C\#\)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Reordenar parámetros de refactorización \(C\#\)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## Refactorización de varios proyectos  
 Visual Studio admite la refactorización de varios proyectos que se encuentran en la misma solución.  Todas las operaciones de refactorización que corrigen referencias entre archivos corrigen dichas referencias entre todos los proyectos del mismo lenguaje.  Esto sólo funciona en referencias entre proyectos.  Por ejemplo, si tiene una aplicación de consola que haga referencia a una biblioteca de clases, al cambiar el nombre a un tipo de biblioteca de clases \(mediante la operación de refactorización `Rename`\), también se actualizarán las referencias al tipo de biblioteca de clases en la aplicación de consola.  
  
## Vista previa de los cambios  
 Muchas operaciones de refactorización proporcionan la posibilidad de revisar todos los cambios de referencias que realiza una operación de refactorización en el código, antes de aplicar dichos cambios.  Para estas operaciones de refactorización, aparecerá una opción **Vista previa de los cambios de referencia** en el cuadro de diálogo de refactorización.  Después de seleccionar dicha opción y aceptar la operación de refactorización, aparecerá el cuadro de diálogo **Obtener vista previa de cambios**.  Observe que el cuadro de diálogo **Obtener vista previa de cambios** tiene dos vistas.  La vista inferior mostrará el código con todas las actualizaciones de referencias debido a la operación de refactorización.  Si presiona **Cancelar** en el cuadro de diálogo **Obtener vista previa de cambios**, se detendrá la operación de refactorización y el código no sufrirá ningún cambio.  
  
## Advertencias de refactorización  
 Si el compilador no tiene un conocimiento completo del programa y es posible que el motor de refactorización no pueda actualizar todas las referencias apropiadas, se muestra el cuadro de diálogo de advertencia.  Este cuadro de diálogo de advertencia también ofrece la posibilidad de realizar una vista previa del código en el cuadro de diálogo **Obtener vista previa de cambios** antes de confirmar los cambios.  
  
> [!NOTE]
>  Si un método contiene un error de sintaxis \(que el IDE indica con una línea de subrayado ondulada roja\), el motor de refactorización no actualizará las referencias a un elemento dentro de dicho método.  El ejemplo siguiente muestra este comportamiento.  
  
 De forma predeterminada, si ejecuta una operación de refactorización sin realizar una vista previa de los cambios de las referencias y el programa detecta un error de compilación, el entorno de desarrollo mostrará este cuadro de diálogo de advertencia.  
  
 Si ejecuta una operación de refactorización que tiene habilitada la opción **Vista previa de los cambios de referencia** y el programa detecta un error de compilación, el entorno de desarrollo mostrará el siguiente mensaje de advertencia en la parte inferior del cuadro de diálogo **Obtener vista previa de cambios**, en lugar de mostrar el cuadro de diálogo **Advertencia de refactorización**:  
  
 **El proyecto o una de sus dependencias no se compila actualmente.  Puede que las referencias no estén actualizadas.**  
  
 Esta advertencia de refactorización solo está disponible para las operaciones de refactorización que proporcionan la opción **Vista previa de los cambios de referencia**.  
  
## Refactorización tolerante a errores y resultados de comprobación  
 La refactorización tolera errores.  En otros términos, se puede realizar una refactorización en un proyecto que no se puede compilar.  Sin embargo, en estos casos el proceso de refactorización podría no actualizar correctamente las referencias ambiguas.  
  
 El cuadro de diálogo **Resultados de la comprobación** puede notificar si el motor de refactorización detecta errores de la compilación o si detecta que una operación de refactorización hace que, inadvertidamente, una referencia del código se enlace a algo diferente de a lo que estaba enlazada.  
  
 Para activar la característica de resultados de comprobación, en el menú **Herramientas**, haga clic en **Opciones**.  En el cuadro de diálogo **Opciones**, expanda **Editor de texto** y, a continuación, haga clic en **C\#**.  Haga clic en **Avanzada** y active la casilla **Comprobar resultados de refactorización**.  
  
 El cuadro de diálogo **Resultados de la comprobación** distingue entre dos tipos de problemas de reenlace.  
  
### Referencias cuya definición ya no será el símbolo al que se ha cambiado el nombre  
 Este tipo de problema de reenlace se produce cuando una referencia ya no hace referencia a un símbolo cuyo nombre ha cambiado.  Por ejemplo, considere el siguiente código:  
  
```c#  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Si utiliza la refactorización para cambiar el nombre de `a` por `b`, aparece este cuadro de diálogo.  La referencia a la variable `a`, cuyo nombre ha cambiado, ahora se enlaza al parámetro que se pasa al constructor, en lugar de enlazarse al campo.  
  
### Referencias cuya definición pasará a ser el símbolo cuyo nombre ha cambiado  
 Este tipo de problema de reenlace se produce cuando una referencia que antes no hacía referencia al símbolo cuyo nombre ha cambiado, ahora sí hace referencia a él.  Por ejemplo, considere el siguiente código:  
  
```c#  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 Si utiliza la refactorización para cambiar el nombre de `OtherMethod` por `Method`, aparece este cuadro de diálogo.  La referencia de `Main` ahora hace referencia al método sobrecargado que acepta un parámetro `int` en lugar del método sobrecargado que acepta un parámetro `object`.  
  
## Vea también  
 [Utilizar el entorno de desarrollo de Visual C\#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Cómo: Restaurar miniprogramas de refactorización de C\#](../ide/how-to-restore-csharp-refactoring-snippets.md)