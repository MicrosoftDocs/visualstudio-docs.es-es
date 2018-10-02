---
title: Procedimientos recomendados para las pruebas automatizadas de IU | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, best practices
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 41
ms.author: gewarren
manager: douge
ms.openlocfilehash: bc2f84134eb6e8d96b6d9e5f070d2725e438cc62
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577497"
---
# <a name="best-practices-for-coded-ui-tests"></a>Procedimientos recomendados para las pruebas automatizadas de IU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [procedimientos recomendados para pruebas de IU codificadas](https://docs.microsoft.com/visualstudio/test/best-practices-for-coded-ui-tests).  
  
En este tema se describen los procedimientos recomendados para desarrollar pruebas de IU codificadas.  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
## <a name="best-practices"></a>Procedimientos recomendados  
 Utilice las siguientes directrices para crear una prueba de IU codificada flexible.  
  
-   Use el **Generador de pruebas automatizadas de IU** siempre que sea posible.  
  
-   No modifique el archivo `UIMap.designer.cs` directamente. Si lo hace, se sobrescribirán los cambios en el archivo.  
  
-   Cree la prueba como una secuencia de métodos grabados. Para más información sobre cómo registrar un método, vea [Crear pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
-   Cada método grabado debe actuar en una sola página, formulario o cuadro de diálogo. Cree un nuevo método de prueba para cada nueva página, formulario o cuadro de diálogo.  
  
-   Cuando cree un método, utilice un nombre de método descriptivo en lugar del nombre predeterminado. Un nombre descriptivo ayuda a identificar el propósito del método.  
  
-   Siempre que sea posible, limite cada método grabado a 10 acciones o menos. Este enfoque modular facilita la sustitución de un método si cambia la IU.  
  
-   Cree todas las aserciones con el **Generador de pruebas automatizadas de IU**, que agrega automáticamente un método de aserción al archivo `UIMap.Designer.cs`.  
  
-   Si cambia la interfaz de usuario (UI), vuelva a grabar los métodos de prueba o los métodos de aserción, o vuelva a grabar las secciones afectadas de un método de prueba existente.  
  
-   Crear un archivo <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> para cada módulo en la aplicación sometida a prueba. Para obtener más información, consulte [Probar una aplicación grande con varios mapas de IU](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
-   En la aplicación sometida a prueba, utilice nombres descriptivos al crear los controles de IU. Esto proporciona más significado y facilidad de uso a los nombres de control generados automáticamente.  
  
-   Si está creando las aserciones mediante codificación con la API, cree un método para cada aserción en la parte de la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> que está en el archivo `UIMap.cs`. Llame a este método desde el método de prueba para ejecutar la aserción.  
  
-   Si está codificando directamente con la API, utilice en el código las propiedades y los métodos de las clases generadas en el archivo `UIMap.Designer.cs` siempre que pueda. Estas clases hacen que el trabajo sea más fácil y más fiable, y le ayudarán a ser más productivo.  
  
 Las pruebas de IU codificadas se adaptan automáticamente a los numerosos cambios en la interfaz de usuario. Si, por ejemplo, un elemento de la IU ha cambiado de posición o color, la prueba de IU codificada seguirá encontrando el elemento correcto, por lo general.  
  
 Durante una serie de pruebas, el marco de pruebas encuentra los controles de la IU mediante un conjunto de propiedades de búsqueda que se aplican a cada clase de control de las definiciones creadas por el **Generador de pruebas automatizadas de IU** en el archivo `UIMap.Designer.cs`. Las propiedades de búsqueda contienen pares nombre-valor de los nombres de propiedad y los valores de propiedad que pueden utilizarse para identificar el control, como las propiedades <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> y <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> del control. Si se modifican las propiedades de búsqueda, la prueba de IU codificada encontrará correctamente el control en la IU. Si se cambian las propiedades de búsqueda, las pruebas de IU codificadas tienen un algoritmo de coincidencia inteligente que aplica la heurística para buscar ventanas y controles en la IU. Cuando haya cambiado la interfaz de usuario, debe poder modificar las propiedades de búsqueda de elementos identificados anteriormente para asegurarse de que se encuentran correctamente.  
  
## <a name="what-to-do-if-your-user-interface-changes"></a>Qué hacer si cambia la interfaz de usuario  
 Las interfaces de usuario cambian frecuentemente durante el desarrollo. Estas son algunas maneras de reducir el impacto de estos cambios:  
  
-   Busque el método registrado que hace referencia a este control y use el **Generador de pruebas automatizadas de IU** para volver a registrar las acciones de este método. Puede utilizar el propio nombre del método para sobrescribir las acciones existentes.  
  
-   Si un control tiene una aserción que ya no es válida:  
  
    -   Elimine el método que contiene la aserción.  
  
    -   Quite la llamada a este método desde el método de prueba.  
  
    -   Agregue una aserción nueva arrastrando el botón de cruz hasta el control de la IU, abra la asignación de IU y agregue la nueva aserción.  
  
 Para más información sobre cómo registrar pruebas automatizadas de IU, vea [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md).  
  
## <a name="what-to-do-if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Qué hacer si se debe completar un proceso en segundo plano antes de continuar con la prueba  
 Tal vez tenga que esperar a que finalice un proceso antes de continuar con la siguiente acción de la interfaz de usuario. Para ello, puede usar <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> para esperar antes de que continúe la prueba, como en el ejemplo siguiente.  
  
```  
// Set the playback to wait for all threads to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;  
  
// Press the submit button  
this.UIMap.ClickSubmit();  
  
// Reset the playback to wait only for the UI thread to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;  
```  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting>   
 [Usar UI Automation para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Probar una aplicación grande con varios mapas de IU](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



