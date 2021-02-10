---
title: Compatibilidad con árabe y hebreo
description: Descubra cómo mostrar textos en árabe y hebreo y cómo escribir texto bidireccional para los valores y los nombres de objetos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a16aa4d445878ac8d357fa551e46552a1465bfe1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971354"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Compatibilidad con idiomas bidireccionales en Visual Studio

Visual Studio puede mostrar el texto en árabe y hebreo correctamente y permite escribir texto bidireccional para valores y nombres de objetos.

> [!NOTE]
> Para escribir y mostrar idiomas bidireccionales, debe trabajar con una versión de Windows que esté configurada con el idioma apropiado. Puede ser una versión en inglés de Windows con el paquete de idioma correspondiente instalado o la versión de Windows localizada según corresponda.

## <a name="fully-supported-features"></a>Características totalmente compatibles

En tiempo de diseño en Visual Studio, puede usar idiomas bidireccionales al escribir texto, al asignar nombres a objetos y al guardar y abrir archivos.

### <a name="text-entry"></a>Entrada de texto

Visual Studio admite Unicode, por lo que si el sistema está establecido en la configuración regional y el idioma de entrada adecuados, puede escribir texto en árabe o hebreo. (La compatibilidad con el árabe incluye kashida y diacríticos).

### <a name="arabic-or-hebrew-object-names"></a>Nombres de objeto en árabe o hebreo

Puede usar idiomas bidireccionales para asignar nombres a soluciones, proyectos, archivos, carpetas, etc. En el código, puede usar idiomas bidireccionales para los nombres de variables, clases, objetos, atributos, metadatos y otros elementos. Al trabajar con el árabe, puede usar cualquier carácter árabe, incluidos kashida y diacríticos.

A los siguientes elementos se les puede asignar nombre en árabe o hebreo y Visual Studio los administra correctamente:

- Nombres de solución, proyecto y archivo, incluidas las carpetas que incluya en la ruta de acceso del proyecto.

   El **Explorador de soluciones** muestra los nombres de elemento y solución correctamente.

- Contenido de los archivos.

   Puede abrir o guardar archivos con codificación Unicode o con una página de código seleccionada.

- Elementos de datos.

   El **Explorador de servidores** muestra estos elementos correctamente y permite editarlos.

- Elementos copiados en el Portapapeles de Windows.

- Atributos y metadatos.

- Valores de propiedad

   Puede usar texto en árabe o hebreo en la ventana **Propiedades**. La ventana le permite cambiar entre la lectura de derecha a izquierda y de izquierda a derecha mediante las pulsaciones de tecla estándar de Windows (**Ctrl**+**Mayús Der** para el sentido de derecha a izquierda y **Ctrl**+**Mayús Izq** para el sentido de izquierda a derecha).

- Código y texto literal.

   En el editor de código, puede usar el árabe o el hebreo para asignar nombres a clases, funciones, variables, propiedades, literales de cadena, atributos, etc. En cambio, el editor no admite la lectura de derecha a izquierda; el texto siempre comienza en el margen izquierdo.

   > [!TIP]
   > Se recomienda colocar los literales de cadena en archivos de recursos en lugar de codificarlos de forma rígida en los programas. Para obtener más información, vea [Recursos de aplicaciones de escritorio (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > Debe ser coherente en cómo hace referencia a los objetos denominados en árabe y hebreo. Por ejemplo, si usa kashida para designar una variable en árabe, debe usar siempre kashida cuando haga referencia a esa variable o, de lo contrario, se producirán errores.

- Comentarios en código. Puede crear comentarios en árabe o hebreo. También puede usar estos idiomas en la herramienta de generador de comentarios.

### <a name="file-encoding"></a>Codificación de archivos

Puede guardar y abrir archivos con una codificación Unicode o específica del idioma. Para obtener más información, vea [Cómo: Guardar y abrir archivos con codificación](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Lectura de derecha a izquierda

Visual Studio tiene compatibilidad limitada con el orden de lectura de derecha a izquierda. De manera predeterminada, los controles de entrada de texto de Visual Studio usan la lectura de izquierda a derecha. En la mayoría de los casos, puede usar gestos estándar de Windows para cambiar el sentido de la lectura. Por ejemplo, puede presionar **Ctrl**+**Mayús Der** para cambiar la ventana **Propiedades** para que admita la lectura de derecha a izquierda de valores de propiedad.

El orden de lectura de derecha a izquierda no se admite en las siguientes ubicaciones de Visual Studio:

- Las casillas, listas desplegables y otros controles de cuadros de diálogo de Visual Studio usan siempre la lectura de izquierda a derecha.

- El editor de código y el editor de texto no admiten la lectura de derecha a izquierda. Puede escribir texto en un idioma bidireccional, pero el sentido de la lectura siempre es de izquierda a derecha.

## <a name="see-also"></a>Consulte también

- [Desarrollo de aplicaciones localizadas y globalizadas](globalizing-and-localizing-applications.md)
