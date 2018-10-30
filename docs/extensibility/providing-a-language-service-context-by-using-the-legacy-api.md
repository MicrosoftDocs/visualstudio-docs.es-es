---
title: Proporcionar un contexto de servicio de lenguaje a través de la API heredada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67ff7d911ef0cdd3debd920ac85e9e3265a619e3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909963"
---
# <a name="provide-a-language-service-context-by-using-the-legacy-api"></a>Proporcionar un contexto de servicio de lenguaje mediante la API heredada
Hay dos opciones para un servicio de lenguaje proporcionar el contexto de usuario mediante el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor básico: proporcionar un contexto de marcador de texto o proporcionan todo el contexto de usuario. A continuación se describen las diferencias entre cada uno.  
  
 Para obtener más información sobre lo que proporciona contexto a un servicio de lenguaje que está conectado a su propio editor, vea [Cómo: proporcionar el contexto para los editores](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Proporcionar un contexto de marcador de texto en el editor  
 Para proporcionar contexto para los errores del compilador indicados por los marcadores de texto en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de núcleo, implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaz. En este escenario, el servicio de lenguaje proporciona contexto solo cuando el cursor está en un marcador de texto. Esto permite que el editor proporcionar la palabra clave en el cursor a la **Ayuda dinámica** ventana sin atributos.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Proporcione todo el contexto de usuario en el editor  
 Si está creando un servicio de lenguaje y está usando el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core editor, a continuación, puede implementar el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaz para proporcionar contexto para el servicio de lenguaje.  
  
 Para la implementación de `IVsLanguageContextProvider`, un contenedor de contexto (colección) se adjunta al editor, que es responsable de actualizar el contenedor de contexto. Cuando el **Ayuda dinámica** ventana llamadas la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interfaz en este contenedor de contextos en tiempo de inactividad, el contenedor de contexto consulta el editor para una actualización. El editor, a continuación, notifica al servicio de lenguaje que debe actualizar el editor y pasa un puntero al contenedor de contexto. Esto se realiza mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> método desde el editor para el servicio de lenguaje. Con el puntero para el contenedor de contexto, el servicio de lenguaje ahora puede agregar y quitar atributos y palabras clave. Para obtener más información, consulta <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Hay dos maneras diferentes de implementar `IVsLanguageContextProvider`:  
  
- Proporcionan una palabra clave para el contenedor de contexto  
  
   Cuando el editor se llama para actualizar el contenedor de contexto, pase los atributos y palabras clave adecuadas y, a continuación, devolver `S_OK`. Este valor devuelto indica el editor para conservar el contexto de la palabra clave y el atributo, en lugar de proporcionar la palabra clave en la posición del cursor para el contenedor de contexto.  
  
- Obtener la palabra clave de la palabra clave en la posición del cursor  
  
   Cuando el editor se llama para actualizar el contenedor de contexto, pase los atributos adecuados y, a continuación, devolver `E_FAIL`. Este valor devuelto indica el editor para conservar los atributos en el contenedor de contexto, pero actualizar el contenedor de contexto con la palabra clave en la posición del cursor.  
  
  El diagrama siguiente muestra cómo se proporciona el contexto para un servicio de lenguaje que implementa `IVsLanguageContextProvider`.  
  
  ![Gráfico de LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Contexto para un servicio de lenguaje  
  
  Como puede ver en el diagrama, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de texto básico tiene un contenedor de contexto asociado a él. Este contenedor de contextos apunta a tres contenedores de subcontextos independientes: servicio de lenguaje, el editor predeterminado y marcador de texto. Los contenedores de subcontexto language service y el texto marcador contengan atributos y palabras clave para el servicio de lenguaje, si la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> se implementa la interfaz y marcadores de texto si el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> implementan la interfaz. Si no implementa alguna de estas interfaces, el editor proporciona contexto para la palabra clave en la posición del cursor en el contenedor del subcontexto de editor predeterminado.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Directrices de contexto para los editores y diseñadores  
 Diseñadores y editores deben proporcionar una palabra clave general en la ventana de diseñador o editor. Esto se hace para que un tema de ayuda genérico, pero es adecuado, se mostrará para el diseñador o editor cuando el usuario presiona **F1**. Un editor debe, además, proporcione la palabra clave actual en la posición del cursor o proporcionar un término clave según la selección actual. Esto se hace para garantizar que un tema de ayuda para el texto o un elemento de interfaz de usuario que señala o seleccionada aparecerá cuando el usuario presiona **F1**. Un diseñador proporciona contexto para un elemento seleccionado en un diseñador, como un botón en un formulario. Los editores y diseñadores también deben conectarse a un servicio de lenguaje como se describe en [Fundamentos de servicio de lenguaje heredado](../extensibility/internals/legacy-language-service-essentials.md).