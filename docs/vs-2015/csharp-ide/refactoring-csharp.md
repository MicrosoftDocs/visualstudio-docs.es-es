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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667498"
---
# <a name="refactoring-c"></a>Refactorización (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La refactorización es el proceso de mejorar el código una vez que se ha escrito cambiando la estructura interna del código sin cambiar el comportamiento externo del código.

 Visual C# proporciona los siguientes comandos de refactorización en el menú **refactorizar** :

- [Extraer refactorización de método (C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [Cambiar nombre de refactorización (C#)](../csharp-ide/rename-refactoring-csharp.md)

- [Encapsular refactorización de campo (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [Extraer refactorización de interfaz (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [Quitar refactorización de parámetros (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [Reordenar refactorización de parámetros (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>Refactorización de varios proyectos
 Visual Studio admite la refactorización de varios proyectos para los proyectos que se encuentran en la misma solución. Todas las operaciones de refactorización que corrigen referencias en archivos corrigen esas referencias en todos los proyectos del mismo idioma. Esto funciona con cualquier referencia de proyecto a proyecto. Por ejemplo, si tiene una aplicación de consola que hace referencia a una biblioteca de clases, al cambiar el nombre de un tipo de biblioteca de clases (mediante la `Rename` operación de refactorización), también se actualizan las referencias al tipo de biblioteca de clases en la aplicación de consola.

## <a name="changes-preview"></a>Vista previa de cambios
 Muchas operaciones de refactorización proporcionan una oportunidad para revisar todos los cambios de referencia que llevaría a cabo una operación de refactorización en el código antes de confirmar dichos cambios. Para estas operaciones de refactorización, aparecerá una opción **vista previa de los cambios de referencia** en el cuadro de diálogo refactorización. Después de seleccionar esa opción y aceptar la operación de refactorización, aparecerá el **cuadro de diálogo vista previa de los cambios** . Tenga en cuenta que el cuadro de diálogo **vista previa de los cambios** tiene dos vistas. La vista inferior mostrará el código con todas las actualizaciones de referencia debido a la operación de refactorización. Si presiona **Cancelar** en el cuadro de diálogo **vista previa de los cambios** , se detendrá la operación de refactorización y no se realizarán cambios en el código.

## <a name="refactoring-warnings"></a>Refactorizar advertencias
 Si el compilador no tiene un conocimiento completo del programa y es posible que el motor de refactorización no actualice todas las referencias adecuadas, se muestra el cuadro de diálogo de advertencia. Este cuadro de diálogo de advertencia también le permite obtener una vista previa del código en el cuadro de diálogo **vista previa de los cambios** antes de confirmar los cambios.

> [!NOTE]
> Si un método contiene un error de sintaxis (que el IDE indica con un subrayado ondulado de color rojo), el motor de refactorización no actualizará ninguna referencia a un elemento dentro de ese método. En el ejemplo siguiente se muestra este comportamiento.

 De forma predeterminada, si ejecuta una operación de refactorización sin obtener una vista previa de los cambios de referencia y se detecta un error de compilación en el programa, el entorno de desarrollo muestra este cuadro de diálogo de advertencia.

 Si ejecuta una operación de refactorización que tiene habilitados **los cambios de referencia de vista previa** y se detecta un error de compilación en el programa, el entorno de desarrollo mostrará el siguiente mensaje de advertencia en la parte inferior del cuadro de diálogo **vista previa de los cambios** , en lugar de mostrar el cuadro de diálogo **Advertencia de refactorización** :

 **El proyecto o una de sus dependencias no se compilan actualmente. Es posible que las referencias no se actualicen.**

 Esta advertencia de refactorización solo está disponible para las operaciones de refactorización que proporcionan la opción **vista previa de los cambios de referencia** .

## <a name="error-tolerant-refactoring-and-verification-results"></a>Resultados de la refactorización y comprobación tolerantes a errores
 La refactorización es tolerante a errores. En otras palabras, puede realizar una refactorización en un proyecto que no se puede compilar. Sin embargo, en estos casos, es posible que el proceso de refactorización no actualice las referencias ambiguas correctamente.

 El cuadro de diálogo resultados de la **comprobación** puede notificarle si el motor de refactorización detecta errores de compilación o detecta que una operación de refactorización provoca involuntariamente que una referencia de código se enlace con algo diferente de la que estaba enlazada originalmente (problema de reenlace).

 Para activar la característica resultados de la comprobación, en el menú **herramientas** , haga clic en **Opciones**. En el cuadro de diálogo **Opciones** , expanda **Editor de texto**y, a continuación, expanda **C#**. Haga clic en **avanzadas** y active la casilla **comprobar resultados de refactorización** .

 El cuadro de diálogo resultados de la **comprobación** distingue la diferencia entre dos tipos de problemas de reenlace.

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

 Si usa la refactorización para cambiar el nombre `a` a `b` , aparece este cuadro de diálogo. La referencia a la variable con el nombre cambiado `a` ahora se enlaza al parámetro que se pasa al constructor en lugar de enlazarse al campo.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Referencias cuya definición se convertirá ahora en el símbolo cuyo nombre ha cambiado
 Este tipo de problema de reenlace se produce cuando una referencia que anteriormente no hacía referencia al símbolo cuyo nombre ha cambiado ahora hace referencia al símbolo cuyo nombre ha cambiado. Por ejemplo, considere el siguiente código:

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

 Si usa la refactorización para cambiar el nombre `OtherMethod` a `Method` , aparece este cuadro de diálogo. La referencia en `Main` ahora hace referencia al método sobrecargado que acepta un `int` parámetro en lugar del método sobrecargado que acepta un `object` parámetro.

## <a name="see-also"></a>Consulte también
 [Usar el entorno de desarrollo de Visual Studio para c#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [Cómo: restaurar fragmentos de código de refactorización de c#](../ide/how-to-restore-csharp-refactoring-snippets.md)