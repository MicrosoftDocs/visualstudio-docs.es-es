---
title: Refactorización (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 78ac19ac0e992b51affdbf6a0e6e3268ddfa52d0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997238"
---
# <a name="refactoring-c"></a>Refactorización (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La refactorización es el proceso de mejorar el código una vez que se ha escrito cambiando la estructura interna del código sin cambiar el comportamiento del código externo.  
  
 Visual C# proporciona los siguientes comandos de refactorización en el **refactorización** menú:  
  
-   [Extraer refactorización de método (C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Cambiar nombre de refactorización (C#)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Encapsular refactorización de campo (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Extraer refactorización de interfaz (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Quitar refactorización de parámetros (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Reordenar refactorización de parámetros (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>Refactorización de varios proyectos  
 Visual Studio admite la refactorización de varios proyectos para proyectos que se encuentran en la misma solución. Todas las operaciones de refactorización que corrigen referencias entre archivos corrigen esas referencias a todos los proyectos del mismo idioma. Esto funciona para todas las referencias de proyecto a proyecto. Por ejemplo, si tiene una aplicación de consola que se hace referencia a una biblioteca de clases, al cambiar el nombre de un tipo de biblioteca de clases (mediante el `Rename` operación de refactorización), también se actualizan las referencias al tipo de la biblioteca de clases en la aplicación de consola.  
  
## <a name="changes-preview"></a>Vista previa de cambios  
 Muchas operaciones de refactorización proporcionan una oportunidad revisar todos los cambios de referencia que realizaría una operación de refactorización en el código, antes de confirmar los cambios. Para estas operaciones, la refactorización un **obtener una vista previa de los cambios de referencia** opción volverá a aparecer en el cuadro de diálogo de refactorización. Después de seleccionar la opción y aceptar la operación de refactorización, la **cuadro de diálogo de vista previa de cambios** aparecerá. Tenga en cuenta que el **vista previa de cambios** cuadro de diálogo tiene dos vistas. La vista de la parte inferior se mostrará el código con todas las actualizaciones de referencia debido a la operación de refactorización. Al presionar **cancelar** en el **vista previa de cambios** cuadro de diálogo detendrá la operación de refactorización y no se realizará ningún cambio en el código.  
  
## <a name="refactoring-warnings"></a>Advertencias de refactorización  
 Si el compilador no tiene una descripción completa del programa, y es posible que el motor de refactorización no pueda actualizar todas las referencias adecuadas, se muestra el cuadro de diálogo de advertencia. Este cuadro de diálogo de advertencia también proporciona una oportunidad para obtener una vista previa del código en el **vista previa de cambios** cuadro de diálogo antes de confirmar los cambios.  
  
> [!NOTE]
>  Si un método contiene un error de sintaxis (lo que significa que el IDE con un subrayado ondulado rojo), el motor de refactorización no actualizará todas las referencias a un elemento dentro de ese método. El ejemplo siguiente muestra este comportamiento.  
  
 De forma predeterminada, si ejecuta cambia de una operación de refactorización sin vista previa de referencia y se detecta un error de compilación en el programa, a continuación, el entorno de desarrollo muestra este cuadro de diálogo de advertencia.  
  
 Si ejecuta una operación de refactorización que tiene **vista previa de cambios de referencia** habilitado y se detecta un error de compilación en el programa y, a continuación, el entorno de desarrollo mostrará el siguiente mensaje de advertencia en la parte inferior de la **Vista previa de cambios** cuadro de diálogo, en lugar de mostrar el **advertencia refactorización** cuadro de diálogo:  
  
 **El proyecto o alguna de sus dependencias no se puede generar actualmente. No se pueden actualizar las referencias.**  
  
 Esta advertencia de refactorización solo está disponible para operaciones de refactorización que proporcionan la **vista previa de cambios de referencia** opción.  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>Refactorización tolerante a errores y resultados de la comprobación  
 La refactorización es tolerante a errores. En otras palabras, puede realizar una refactorización en un proyecto que no se puede compilar. Sin embargo, en estos casos el proceso de refactorización podría no actualizar referencias ambiguas correctamente.  
  
 El **resultados de la comprobación** cuadro de diálogo le notifica si el motor de refactorización detecta errores de compilación o detecta que una operación de refactorización accidentalmente hace una referencia de código enlazar a algo diferente de lo que era que originalmente se enlaza a (problema de reenlace).  
  
 Activar los resultados de la comprobación de la característica, en el **herramientas** menú, haga clic en **opciones**. En el **opciones** cuadro de diálogo, expanda **Editor de texto**y, a continuación, expanda **C#**. Haga clic en **avanzadas** y seleccione el **comprobar resultados de refactorización** casilla de verificación.  
  
 El **resultados de la comprobación** cuadro de diálogo distingue la diferencia entre dos tipos de problemas de reenlace.  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Referencias cuya definición ya no será el símbolo cuyo nombre ha cambiado  
 Este tipo de problema de reenlace se produce cuando una referencia ya no hace referencia a un símbolo cuyo nombre ha cambiado. Por ejemplo, considere el siguiente código:  
  
```csharp  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Si utiliza la refactorización para cambiar el nombre `a` a `b`, aparece este cuadro de diálogo. La referencia a la variable cuyo nombre ha cambiado `a` ahora éste enlaza al parámetro que se pasa al constructor en lugar de enlazar el campo.  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Referencias cuya definición ahora se convertirá en el símbolo cuyo nombre ha cambiado  
 Este tipo de problema de reenlace se produce cuando una referencia que antes no hacía referencia al símbolo cuyo nombre ha cambiado ahora hace referencia al símbolo cuyo nombre ha cambiado. Por ejemplo, considere el siguiente código:  
  
```csharp  
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
  
 Si utiliza la refactorización para cambiar el nombre `OtherMethod` a `Method`, aparece este cuadro de diálogo. La referencia en `Main` ahora hace referencia al método sobrecargado que acepta un `int` parámetro en lugar del método sobrecargado que acepta un `object` parámetro.  
  
## <a name="see-also"></a>Vea también  
 [Uso del entorno de desarrollo de Visual Studio para C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Cómo: Restaurar fragmentos de código de refactorización de C#](../ide/how-to-restore-csharp-refactoring-snippets.md)