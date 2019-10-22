---
title: Herramientas de localización
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 934427c2bfba769968b7aeb364625b71af47eca7
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820871"
---
# <a name="develop-globalized-and-localized-apps"></a>Desarrollo de aplicaciones localizadas y globalizadas

Visual Studio facilita el desarrollo para destinatarios internacionales al aprovechar los servicios integrados en [.NET](/dotnet/standard/globalization-localization/).

Por ejemplo, el sistema de proyectos para aplicaciones de Windows Forms puede generar archivos de recursos para la referencia cultural de la UI de reserva y para cada una de las referencias culturales de UI adicionales. Al compilar un proyecto en Visual Studio, los archivos de recursos se compilan desde el formato XML de Visual Studio (.resx) en un formato binario intermedio (.resources), que se inserta después en ensamblados satélite. Para obtener más información, consulte [Archivos de recursos en Visual Studio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) y [Crear ensamblados satélite para aplicaciones de escritorio](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Lenguajes bidireccionales

Puede usar Visual Studio para crear aplicaciones que muestren correctamente el texto en idiomas que se escriben de derecha a izquierda, como el árabe y el hebreo. Para algunas características, simplemente puede establecer propiedades. En otros casos, debe implementar características en el código.

> [!NOTE]
> Para escribir y mostrar idiomas bidireccionales, debe trabajar con una versión de Windows que esté configurada con el idioma apropiado. Puede ser una versión en inglés de Windows con el paquete de idioma correspondiente instalado o la versión de Windows localizada según corresponda.

### <a name="apps-that-support-bidirectional-languages"></a>Aplicaciones que admiten idiomas bidireccionales

- Aplicaciones de Windows

   Puede crear aplicaciones completamente bidireccionales que incluyan compatibilidad con texto bidireccional, la lectura de derecha a izquierda y creación de reflejo (inversión del diseño de ventanas, menús, cuadros de diálogo, etc.). Excepto la creación de reflejo, estas características están disponibles de manera predeterminada o como valores de propiedad. La creación de reflejo se admite intrínsecamente para algunas características, como los cuadros de mensaje. En cambio, en otros casos debe implementar la creación de reflejo en el código. Para obtener más información, consulte [Compatibilidad bidireccional en las aplicaciones de Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Aplicaciones web

   Los servicios web admiten el envío y la recepción de texto Unicode y UTF-8, lo que los convierte en aptos para aplicaciones que implican idiomas bidireccionales. Las aplicaciones cliente web basan la interfaz de usuario en exploradores, por lo que el grado de compatibilidad bidireccional en una aplicación web depende de cómo admita el explorador del usuario esas características bidireccionales. En Visual Studio, puede crear aplicaciones compatibles con texto árabe o hebreo, lectura de derecha a izquierda, codificación de archivos y configuración de la referencia cultural local. Para más información, consulte [Compatibilidad bidireccional para aplicaciones web ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

> [!NOTE]
> Las aplicaciones de consola no incluyen compatibilidad con texto de idiomas bidireccionales. Esta es una consecuencia de cómo funciona Windows con las aplicaciones de consola.

## <a name="see-also"></a>Vea también

- [Compatibilidad con idiomas bidireccionales en Visual Studio](use-bidirectional-languages.md)
- [Globalización y localización de aplicaciones .NET](/dotnet/standard/globalization-localization/)
- [Recursos en aplicaciones .NET](/dotnet/framework/resources/)