---
title: Procedimientos recomendados para las pruebas automatizadas de IU
description: Conozca las recomendaciones para desarrollar pruebas automatizadas de IU. Estas directrices ayudan a crear una prueba automatizada de IU flexible.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a4a79ca397b46d06e18c62fde2034551ff7afe0
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441812"
---
# <a name="best-practices-for-coded-ui-tests"></a>Procedimientos recomendados para las pruebas de IU codificadas

En este tema se describen algunas recomendaciones para el desarrollo de pruebas automatizadas de IU.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>Procedimientos recomendados

Utilice las siguientes directrices para crear una prueba de IU codificada flexible.

- Use el **Generador de pruebas automatizadas de IU** siempre que sea posible.

- No modifique directamente el archivo *UIMap.Designer.cs*. Si lo hace, se sobrescribirán los cambios en el archivo.

- Cree la prueba como una secuencia de métodos grabados. Para obtener más información sobre cómo registrar un método, vea [Crear pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md).

- Cada método grabado debe actuar en una sola página, formulario o cuadro de diálogo. Cree un nuevo método de prueba para cada nueva página, formulario o cuadro de diálogo.

- Cuando cree un método, utilice un nombre de método descriptivo en lugar del nombre predeterminado. Un nombre descriptivo ayuda a identificar el propósito del método.

- Siempre que sea posible, limite cada método grabado a 10 acciones o menos. Este enfoque modular facilita la sustitución de un método si cambia la IU.

- Cree todas las aserciones con el **Generador de pruebas automatizadas de IU**, que agrega automáticamente un método de aserción al archivo *UIMap.Designer.cs*.

- Si cambia la interfaz de usuario (UI), vuelva a grabar los métodos de prueba o los métodos de aserción, o vuelva a grabar las secciones afectadas de un método de prueba existente.

- Cree un archivo [UIMap](/previous-versions/dd580454(v=vs.140)) separado para cada módulo de la aplicación bajo prueba. Para obtener más información, vea [Probar una aplicación grande con varios mapas de IU](../test/testing-a-large-application-with-multiple-ui-maps.md).

- En la aplicación sometida a prueba, utilice nombres descriptivos al crear los controles de IU. Esto proporciona más significado y facilidad de uso a los nombres de control generados automáticamente.

- Si está creando las aserciones mediante codificación con la API, cree un método para cada aserción en la parte de la clase [UIMap](/previous-versions/dd580454(v=vs.140)) que está en el archivo *UIMap.cs*. Para ejecutar la aserción, llame a este método desde el método de prueba.

- Si está codificando directamente con la API, utilice en el código las propiedades y los métodos de las clases generadas en el archivo *UIMap.Designer.cs* siempre que pueda. Estas clases hacen que el trabajo sea más fácil y más fiable, y le ayudarán a ser más productivo.

Las pruebas de IU codificadas se adaptan automáticamente a los numerosos cambios en la interfaz de usuario. Si, por ejemplo, un elemento de la IU ha cambiado de posición o color, la prueba de IU codificada seguirá encontrando el elemento correcto, por lo general.

Durante la ejecución de una prueba, el marco de pruebas utiliza un conjunto de propiedades de búsqueda para localizar los controles de interfaz de usuario. Las propiedades de búsqueda se aplican a cada clase de control de las definiciones creadas por el **Generador de pruebas automatizadas de IU** en el archivo *UIMap.Designer.cs*. Las propiedades de búsqueda contienen pares nombre-valor de los nombres de propiedad y los valores de propiedad que pueden utilizarse para identificar el control, como las propiedades <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> y <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> del control. Si se modifican las propiedades de búsqueda, la prueba de IU codificada encontrará correctamente el control en la IU. Si se cambian las propiedades de búsqueda, las pruebas automatizadas de IU tienen un algoritmo de coincidencia inteligente que aplica la heurística para buscar ventanas y controles en la interfaz de usuario. Cuando haya cambiado la interfaz de usuario, debe poder modificar las propiedades de búsqueda de elementos identificados anteriormente para asegurarse de que se encuentran correctamente.

## <a name="if-your-user-interface-changes"></a>Si cambia la interfaz de usuario

Las interfaces de usuario cambian frecuentemente durante el desarrollo. Estas son algunas maneras de reducir el impacto de estos cambios:

- Busque el método registrado que hace referencia a este control y use el **Generador de pruebas automatizadas de IU** para volver a registrar las acciones de este método. Puede utilizar el propio nombre del método para sobrescribir las acciones existentes.

- Si un control tiene una aserción que ya no es válida:

  - Elimine el método que contiene la aserción.

  - Quite la llamada a este método desde el método de prueba.

  - Agregue una aserción nueva arrastrando el botón de cruz hasta el control de la IU, abra la asignación de IU y agregue la nueva aserción.

Para obtener más información sobre cómo registrar pruebas automatizadas de IU, vea [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Si se debe completar un proceso en segundo plano antes de continuar con la prueba

Tal vez tenga que esperar a que finalice un proceso antes de continuar con la siguiente acción de la interfaz de usuario. Para ello, puede usar <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> para esperar antes de que continúe la prueba, como en el ejemplo siguiente:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Consulte también

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Usar la automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
- [Crear pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md)
- [Probar una aplicación grande con varios mapas de IU](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Configuraciones y plataformas compatibles con las pruebas automatizadas de IU y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
