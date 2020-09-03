---
title: Proporcionar un contexto de servicio de lenguaje mediante la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193868"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Proporcionar un contexto de servicio de lenguaje mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay dos opciones para que un servicio de lenguaje proporcione el contexto de usuario mediante el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor básico: proporcionar un contexto de marcador de texto o proporcionar todo el contexto de usuario. Aquí se describen las diferencias entre cada una de ellas.  
  
 Para obtener más información sobre cómo proporcionar contexto a un servicio de lenguaje que está conectado a su propio editor, consulte [Cómo: proporcionar contexto para editores](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Proporcionar contexto de marcador de texto al editor  
 Para proporcionar contexto para los errores del compilador que indican los marcadores de texto en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal, implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfaz. En este escenario, el servicio de lenguaje proporciona contexto solo cuando el cursor está en un marcador de texto. Esto permite que el editor proporcione la palabra clave en el cursor a la ventana de **Ayuda dinámica** sin atributos.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Proporcionar todo el contexto de usuario al editor  
 Si va a crear un servicio de lenguaje y usa el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor básico, puede implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfaz para proporcionar el contexto para su servicio de lenguaje.  
  
 Para la implementación de `IVsLanguageContextProvider` , se adjunta un contenedor de contexto (colección) al editor, que es responsable de actualizar el contenedor de contextos. Cuando la ventana **Ayuda dinámica** llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interfaz de este contenedor de contextos en tiempo de inactividad, el contenedor de contextos consulta el editor para obtener una actualización. A continuación, el editor notifica al servicio de lenguaje que debe actualizar el editor y pasa un puntero al contenedor de contextos. Esto se hace llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> método desde el editor al servicio de lenguaje. Con el puntero al contenedor de contexto, el servicio de lenguaje ahora puede Agregar y quitar atributos y palabras clave. Para obtener más información, vea <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Hay dos maneras diferentes de implementar `IVsLanguageContextProvider` :  
  
- Proporcionar una palabra clave al contenedor de contextos  
  
   Cuando se llama al editor para actualizar el contenedor de contextos, pase las palabras clave y atributos adecuados y, a continuación, devuelva `S_OK` . Este valor devuelto indica al editor que conserve la palabra clave y el contexto del atributo en lugar de proporcionar la palabra clave en el cursor al contenedor de contextos.  
  
- Obtiene la palabra clave de la palabra clave en el cursor.  
  
   Cuando se llama al editor para actualizar el contenedor de contextos, pase los atributos adecuados y, a continuación, devuelva `E_FAIL` . Este valor devuelto indica al editor que conserve los atributos en el contenedor de contextos, pero actualiza el contenedor de contextos con la palabra clave en el cursor.  
  
  En el diagrama siguiente se muestra cómo se proporciona el contexto para un servicio de lenguaje que implementa `IVsLanguageContextProvider` .  
  
  ![Gráfico de LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Contexto para un servicio de lenguaje  
  
  Como puede ver en el diagrama, el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor de texto principal tiene asociado un contenedor de contexto. Este contenedor de contexto apunta a tres bolsas de subcontexto independientes: servicio de lenguaje, editor predeterminado y marcador de texto. Los contenedores de subcontextos del servicio de lenguaje y del marcador de texto contienen atributos y palabras clave para el servicio de lenguaje si <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> se implementa la interfaz y marcadores de texto si <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> se implementa la interfaz. Si no implementa ninguna de estas interfaces, el editor proporciona contexto para la palabra clave en el cursor en el contenedor de subcontexto del editor predeterminado.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Directrices de contexto para editores y diseñadores  
 Los diseñadores y editores deben proporcionar una palabra clave general para la ventana del editor o del diseñador. Esto se hace para que se muestre un tema de ayuda genérico, pero adecuado, para el diseñador o el editor cuando un usuario presiona F1. Además, un editor debe proporcionar la palabra clave Current en el cursor o proporcionar un término clave basado en la selección actual. Esto se hace para asegurarse de que se muestra un tema de ayuda para el texto o el elemento de la interfaz de usuario señalados o seleccionados cuando el usuario presiona F1. Un diseñador proporciona contexto para un elemento seleccionado en un diseñador, como un botón en un formulario. Los editores y diseñadores también deben conectarse a un servicio de lenguaje, tal como se describe en información esencial sobre el [servicio de lenguaje heredado](../extensibility/internals/legacy-language-service-essentials.md).
