---
title: Clases específicas de las referencias culturales para Windows Forms y formularios Web Forms globales
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8289b44359508d788b43fa155c6f91b58d304138
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Clases específicas de las referencias culturales para Windows Forms y formularios Web Forms globales

Cada referencia cultural tiene distintas convenciones para mostrar fechas, horas, números, moneda y otra información. El espacio de nombres <xref:System.Globalization> contiene clases que pueden usarse para modificar el modo en que se muestran los valores específicos de referencias culturales, como:
- <xref:System.Globalization.DateTimeFormatInfo>
- **Calendar**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>Uso de la configuración de la referencia cultural

Use la configuración de la referencia cultural, almacenada en la aplicación o en el panel de control **Configuración Regional**, para determinar las convenciones culturales en tiempo de ejecución y dar formato a la información en consecuencia. Para obtener más información sobre cómo establecer la referencia cultural, consulte [Cómo: establecer la referencia cultural y la referencia cultural de la interfaz de usuario para la globalización de páginas web de ASP.NET](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Las clases que dan formato automáticamente a la información según la configuración de la referencia cultural se denominan *específicas de referencias culturales*. Algunos métodos específicos de referencias culturales son
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

Algunas funciones específicas de referencias culturales (en el lenguaje Visual Basic) son `MonthName` y `WeekDayName`.

Por ejemplo, el código siguiente muestra cómo puede usar el método <xref:System.IFormattable.ToString%2A> para dar formato a la moneda para la referencia cultural actual:

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))
```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

Si la referencia cultural se establece en "fr-FR", verá lo siguiente en la ventana de salida:

`100,00`

Si la referencia cultural se establece en "en-US", verá lo siguiente en la ventana de salida:

`$100.00`

## <a name="see-also"></a>Vea también

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)