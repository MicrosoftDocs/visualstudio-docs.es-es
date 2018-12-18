---
title: Crear aplicaciones en lenguajes bidireccionales
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f93dea099d9223347c727f3e7a838fcb78d3742
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863639"
---
# <a name="creating-applications-in-bi-directional-languages"></a>Creación de aplicaciones en lenguajes bidireccionales

Puede usar Visual Studio para crear aplicaciones que muestren correctamente el texto en idiomas que se escriben de derecha a izquierda, como el árabe y el hebreo. Para algunas características, simplemente puede establecer propiedades. En otros casos, debe implementar características en el código.

> [!NOTE]
> Para escribir y mostrar idiomas bidireccionales, debe trabajar con una versión de Windows que esté configurada con el idioma apropiado. Puede ser una versión en inglés de Windows con el paquete de idioma correspondiente instalado o la versión de Windows localizada según corresponda.

## <a name="types-of-application-that-support-bi-directional-languages"></a>Tipos de aplicaciones que admiten idiomas bidireccionales

-  Aplicaciones Windows. Puede crear aplicaciones completamente bidireccionales que incluyan compatibilidad con texto bidireccional, la lectura de derecha a izquierda y creación de reflejo (inversión del diseño de ventanas, menús, cuadros de diálogo, etc.). Excepto la creación de reflejo, estas características están disponibles de manera predeterminada o como valores de propiedad. La creación de reflejo se admite intrínsecamente para algunas características, como los cuadros de mensaje. En cambio, en otros casos debe implementar la creación de reflejo en el código. Para más información, consulte [Compatibilidad bidireccional en las aplicaciones de Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

-  Aplicaciones web. Los servicios web admiten el envío y la recepción de texto Unicode y UTF-8, lo que los convierte en aptos para aplicaciones que implican idiomas bidireccionales. Las aplicaciones cliente web basan la interfaz de usuario en exploradores, por lo que el grado de compatibilidad bidireccional en una aplicación web depende de cómo admita el explorador del usuario esas características bidireccionales. En Visual Studio, puede crear aplicaciones compatibles con texto árabe o hebreo, lectura de derecha a izquierda, codificación de archivos y configuración de la referencia cultural local. Para más información, consulte [Compatibilidad bidireccional para aplicaciones web ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

-  Aplicaciones de consola Las aplicaciones de consola no incluyen compatibilidad con texto de idiomas bidireccionales. Esta es una consecuencia de cómo funciona Windows con las aplicaciones de consola.

## <a name="visual-studio-features-that-are-fully-supported"></a>Características de Visual Studio que son totalmente compatibles
 En tiempo de diseño en Visual Studio, puede usar idiomas bidireccionales de las siguientes formas:

-   **Entrada de texto** Visual Studio admite Unicode, por lo que si el sistema está establecido en la configuración regional y el idioma de entrada adecuados, puede escribir texto en árabe o hebreo. (La compatibilidad con el árabe incluye kashida y diacríticos).

-   **Nombres de objetos** Puede usar idiomas bidireccionales para asignar nombres a soluciones, proyectos, archivos, carpetas, etc. En el código, puede usar idiomas bidireccionales para los nombres de variables, clases, objetos, atributos, metadatos y otros elementos.

-   **Codificación de archivo** Puede guardar y abrir archivos con una codificación Unicode o específica del idioma. Para más información, consulte [Cómo: Guardar y abrir archivos con codificación](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-or-no-support"></a>Características con compatibilidad limitada o sin ella
 Otras características comunes a las aplicaciones de idiomas bidireccionales no son completamente compatibles con Visual Studio o, en algunos casos, no son compatibles. Se incluyen los siguientes:

**Lectura de derecha a izquierda** De manera predeterminada, los controles de entrada de texto que usa en Visual Studio usan la lectura de izquierda a derecha. En la mayoría de los casos, puede usar gestos estándar de Windows para cambiar el sentido de la lectura. Por ejemplo, puede pulsar **Ctrl+Mayús Der** para cambiar la ventana **Propiedades** para que admita la lectura de derecha a izquierda de valores de propiedad.

No obstante, la lectura de derecha a izquierda no se admite en todo Visual Studio. Entre las excepciones se incluyen:

-   Las casillas, listas desplegables y otros controles de cuadros de diálogo de Visual Studio usan siempre la lectura de izquierda a derecha.

-   El editor de código y el editor de texto no admiten la lectura de derecha a izquierda. Puede escribir texto en un idioma bidireccional, pero el sentido de la lectura siempre es de izquierda a derecha.

## <a name="naming-things-using-arabic-or-hebrew-text"></a>Asignación de nombres con texto en árabe o hebreo
 Puede usar texto en árabe o hebreo para asignar nombres a carpetas, variables u otros objetos. Al trabajar con el árabe, puede usar cualquier carácter árabe, incluidos kashida y diacríticos.

 A los siguientes elementos se les puede asignar el nombre con texto en árabe o hebreo y se controlarán correctamente en Visual Studio:

-   Nombres de solución, proyecto y archivo, incluidas las carpetas que incluya en la ruta de acceso del proyecto. El **Explorador de soluciones** mostrará los nombres de elemento y solución correctamente.

-   Contenido de los archivos. Puede abrir o guardar archivos con codificación Unicode o con una página de código seleccionada.

    > [!NOTE]
    >  El editor de código es un caso especial. Para obtener detalles, consulte a continuación.

-   Elementos de datos. El **Explorador de servidores** mostrará estos elementos correctamente y permitirá que los edite.

-   Elementos copiados en el Portapapeles de Windows.

-   Atributos y metadatos.

-   Valores de propiedades. Puede usar texto en árabe o hebreo en la ventana **Propiedades**. La ventana le permite cambiar entre la lectura de derecha a izquierda y de izquierda a derecha mediante las pulsaciones de tecla estándar de Windows (**Ctrl+Mayús Der** para el sentido de derecha a izquierda y **Ctrl+Mayús Izq** para el sentido de izquierda a derecha).

-   Código y texto literal. En el editor de código (que también es el editor de texto), puede usar el árabe o hebreo para asignar nombres a clases, funciones, variables, propiedades, literales de cadena, atributos, etc. En cambio, el editor no admite la lectura de derecha a izquierda; el texto siempre comienza en el margen izquierdo.

    > [!TIP]
    > Se recomienda colocar los literales de cadena en archivos de recursos en lugar de codificarlos de forma rígida en los programas. Para obtener más información, vea [Recursos de aplicaciones de escritorio (.NET Framework)](/dotnet/framework/resources/index).

    > [!NOTE]
    > Debe ser coherente en cómo hace referencia a los objetos denominados en estos idiomas. Por ejemplo, si usa kashida para designar una variable en árabe, debe usar siempre kashida cuando haga referencia a esa variable o de lo contrario se producirán errores.

-   Comentarios en código. Puede crear comentarios en árabe o hebreo. También puede usar estos idiomas en la herramienta de generador de comentarios.

## <a name="see-also"></a>Vea también

- [Compatibilidad bidireccional en las aplicaciones de Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)
- [Compatibilidad bidireccional para aplicaciones web ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)
- [Globalizar aplicaciones](../ide/globalizing-applications.md)
- [Localizar aplicaciones](../ide/localizing-applications.md)