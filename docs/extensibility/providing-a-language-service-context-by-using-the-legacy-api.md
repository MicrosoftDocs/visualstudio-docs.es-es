---
title: Proporciona un contexto de servicio de lenguaje mediante la API heredado | Documentos de Microsoft
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
ms.openlocfilehash: 3556fcce3d14d5069854c64d81cb780123a979d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140077"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Proporciona un contexto de servicio de lenguaje mediante la API heredado
Hay dos opciones para un servicio de lenguaje proporcionar el contexto de usuario mediante el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal: proporcionar un contexto de marcador de texto o proporcionar todo el contexto de usuario. A continuación se describen las diferencias entre sí.  
  
 Para obtener más información sobre cómo proporcionar contexto a un servicio de lenguaje que está conectado a su propio editor, consulte [Cómo: proporcionar contexto para los editores](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Proporcionar un contexto de marcador de texto en el Editor  
 Para proporcionar un contexto para errores del compilador indicados por marcadores de texto en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principales del editor, implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaz. En este escenario, el servicio de lenguaje proporciona contexto solo cuando el cursor está en un marcador de texto. Esto permite que el editor proporcionar la palabra clave en el cursor a la **Ayuda dinámica** ventana sin atributos.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Proporcionar todo el contexto de usuario en el Editor  
 Si va a crear un servicio de lenguaje y está usando la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] principales del editor, a continuación, puede implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaz para proporcionar contexto para el servicio de lenguaje.  
  
 Para la implementación de `IVsLanguageContextProvider`, se adjunta un conjunto de contextos (colección) para el editor, que es responsable de actualizar el conjunto de contextos. Cuando el **Ayuda dinámica** ventana llamadas el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interfaz en este contenedor de contexto en tiempo de inactividad, el conjunto de contextos consulta el editor para una actualización. El editor, a continuación, notifica al servicio de lenguaje que se debe actualizar el editor y pasa un puntero a la bolsa de contexto. Esto se realiza mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> método desde el editor para el servicio de lenguaje. Con el puntero a la bolsa de contexto, el servicio de lenguaje ahora puede agregar y quitar atributos y palabras clave. Para obtener más información, consulta <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Hay dos maneras de implementar `IVsLanguageContextProvider`:  
  
-   Proporcionan una palabra clave para el conjunto de contextos  
  
     Cuando el editor se llama para actualizar el conjunto de contextos, pasar en los atributos y las palabras clave adecuadas y, a continuación, devolver `S_OK`. Este valor devuelto indica el editor para conservar el contexto de la palabra clave y el atributo, en lugar de proporcionar la palabra clave en el cursor a la bolsa de contexto.  
  
-   Obtener la palabra clave de la palabra clave en la posición del cursor  
  
     Cuando el editor se llama para actualizar el conjunto de contextos, pasar los atributos adecuados y, a continuación, devolver `E_FAIL`. Este valor devuelto indica el editor para conservar los atributos en el conjunto de contextos, pero para actualizar el conjunto de contextos con la palabra clave en la posición del cursor.  
  
 El diagrama siguiente muestra cómo se proporciona el contexto para un servicio de lenguaje que implementa `IVsLanguageContextProvider`.  
  
 ![Gráfico de LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Contexto para un servicio de lenguaje  
  
 Como puede ver en el diagrama, la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de texto principal tiene una bolsa de contexto asociada a él. Este conjunto de contextos apunta a tres contenedores subcontexto independiente: servicio de lenguaje y editor predeterminado, el marcador de texto. El bolsas lenguaje subcontexto de marcador de servicio y el texto contienen atributos y palabras clave para el servicio de lenguaje si el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> se implementa la interfaz y a los marcadores de texto si el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaz está implementada. Si no implementa cualquiera de estas interfaces, el editor proporciona contexto para la palabra clave en la posición del cursor en la bolsa de subcontexto editor predeterminado.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Directrices de contexto para editores y diseñadores  
 Diseñadores y editores deben proporcionar una palabra clave general para el editor o la ventana del diseñador. Esto se hace para que un tema de ayuda genérico, pero adecuado, se mostrará para el diseñador o editor cuando un usuario presiona la tecla F1. Un editor debe, además, proporcione la palabra clave actual en la posición del cursor o proporcionar un término clave según la selección actual. Esto se hace para asegurarse de que un tema de ayuda para el texto o el elemento de interfaz de usuario que señala o seleccionada aparecerá cuando el usuario presiona la tecla F1. Un diseñador proporciona contexto para un elemento seleccionado en un diseñador, como un botón en un formulario. Editores y diseñadores, también deben conectarse a un servicio de lenguaje tal como se describe en [Essentials de servicio de lenguaje heredado](../extensibility/internals/legacy-language-service-essentials.md).