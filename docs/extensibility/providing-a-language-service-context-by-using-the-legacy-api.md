---
title: "Proporcionar un contexto de servicio de lenguaje a trav&#233;s de la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - el contexto del servicio de lenguaje"
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Proporcionar un contexto de servicio de lenguaje a trav&#233;s de la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay dos opciones para que un servicio de proporcionar contexto de usuario mediante el editor básico de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] : proporciona el contexto de marcador de texto, o proporcione todo el contexto de usuario.  Las diferencias entre cada uno se describen aquí.  
  
 Para obtener más información sobre proporcionar contexto a un servicio de lenguaje que esté conectado a dispone del editor, vea [Cómo: proporcionar contexto para los editores](../extensibility/how-to-provide-context-for-editors.md).  
  
## Proporciona el contexto de marcador de texto al editor  
 Para proporcionar contexto para los errores del compilador indicados por los marcadores de texto en el editor básico de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , implemente la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> .  En este escenario, el servicio de lenguaje proporciona contexto solo cuando el cursor está en un marcador de texto.  Esto permite que el editor proporciona la palabra clave en el cursor a la ventana de **Ayuda dinámica** sin atributos.  
  
## Proporciona el contexto de usuario Todo el editor  
 Si está creando un servicio de lenguaje y utiliza el editor básico de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , puede implementar la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> para proporcionar contexto para el servicio de lenguaje.  
  
 Para la implementación de `IVsLanguageContextProvider`, un contenedor de contexto \(colección\) se asocia al editor, que es responsable de actualizar el contenedor de contexto.  Cuando la ventana de **Ayuda dinámica** llama a la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> en este controlador de contexto en el tiempo de inactividad, el contenedor de contexto el editor para una actualización.  El editor a continuación notifica al servicio de lenguaje que debe actualizar el editor, y pasar un puntero al contenedor de contexto.  Esto se hace llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> de editor al servicio de lenguaje.  Mediante el puntero al contenedor de contexto, el servicio de lenguaje ahora puede agregar y quitar atributos y palabras clave.  Para obtener más información, vea <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Hay dos maneras de implementar `IVsLanguageContextProvider`:  
  
-   Proporcione una palabra clave al contenedor de contexto  
  
     Cuando se llama al editor para actualizar el contenedor de contexto, el paso de las palabras clave adecuadas y los atributos y después devuelven `S_OK`.  Este valor devuelto indica al editor para que el contexto de la palabra clave y el atributo en lugar de la palabra clave en el cursor al contenedor de contexto.  
  
-   Obtiene la palabra clave de la palabra clave en el cursor  
  
     Cuando se llama al editor para actualizar el contenedor de contexto, pase los atributos adecuados y después `E_FAIL`return.  Este valor devuelto indica al editor para que los atributos del contenedor de contexto, pero actualiza el contenedor de contexto con la palabra clave en el cursor.  
  
 El diagrama siguiente se muestra cómo el contexto se proporciona para un servicio de lenguaje que implemente `IVsLanguageContextProvider`.  
  
 ![Gráfico LangServiceImplementation2](../extensibility/media/vslanguageservice2.png "vsLanguageService2")  
Contexto para un servicio de lenguaje  
  
 Como puede ver en el diagrama, el editor de texto básico de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tiene un contenedor de contexto asociado al.  Puntos de este contenedor de contexto a tres bolsas independientes de subcontext: servicio de lenguaje, editor predeterminado, y marcador de texto.  Los bolsas de subcontext de marcador del servicio de lenguaje y de texto contienen atributos y palabras clave para el servicio de lenguaje si se implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> , y marcadores de texto si se implementa la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> .  Si no implementa ninguna de estas interfaces, el editor proporciona el contexto para la palabra clave en el cursor en el contenedor de subcontext de editor predeterminado.  
  
## Instrucciones de contexto para los editores y Diseñadores  
 Los diseñadores y editores deben proporcionar una palabra clave general para la ventana del editor o del diseñador.  Esto se realiza de forma que un genérico, pero un adecuado, tema de Ayuda mostrar para el diseñador o el editor cuando un usuario presiona F1.  Un editor debe, además de esto, proporcionar la palabra clave actual en el cursor o proporcionar un término clave según la selección actual.  Esto se hace garantizar que un tema de Ayuda para el texto o el elemento de la interfaz de usuario designado a o muestra seleccionado cuando el usuario presione F1.  Un contexto de fuentes de diseñador de un elemento seleccionado en un diseñador, como un botón en un formulario.  Los editores y diseñadores también deben conectarse a un servicio de acuerdo con [Fundamentos de servicio de lenguaje heredado](../extensibility/internals/legacy-language-service-essentials.md).