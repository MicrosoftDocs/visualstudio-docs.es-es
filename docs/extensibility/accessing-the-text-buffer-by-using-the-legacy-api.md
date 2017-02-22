---
title: "Acceso al b&#250;fer de texto usando la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - búferes de texto"
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Acceso al b&#250;fer de texto usando la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El texto es responsable de administrar secuencias de texto y la persistencia del archivo.  Aunque el búfer pueda leer o escribir otros formatos, toda la comunicación normal con el búfer se realiza mediante Unicode.  En el antiguo API, el búfer de texto puede utilizar uno o bidimensionales sistemas de coordenadas para identificar ubicaciones de carácter en el búfer.  
  
## Sistemas de coordenadas uno y la Dos\-Dimensión  
 Una posición coordinada unidimensional se basa respecto a una posición de carácter del primer carácter en el búfer, como 147.  Se utiliza la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> para tener acceso a una ubicación unidimensional en el búfer.  Un sistema de coordenadas bidimensional se basa en pares de línea y el índice.  Por ejemplo, un carácter en el búfer en 43, 5 estaría en la línea 43, cinco caracteres a la derecha del primer carácter en esa línea.  Tiene acceso a una ubicación bidimensional en el búfer mediante la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> .  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> y las interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> son implementados por el objeto de búfer de texto \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\) y se puede tener acceso entre sí mediante `QueryInterface`.  El diagrama siguiente muestra estas y otras interfaces de la clave de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Objeto de búfer de texto](../extensibility/media/vstextbuffer.png "vsTextBuffer")  
Objeto de búfer de texto  
  
 Aunque cualquier sistema de coordenadas funcione en el búfer de texto, se optimiza para utilizar coordenadas bidimensionales.  Un sistema de coordenadas unidimensional puede crear sobrecarga de rendimiento.  Por ello, el sistema de coordenadas bidimensional siempre que sea posible.  
  
 La responsabilidad del búfer segundo de texto es la persistencia del archivo.  Para ello, el objeto de búfer de texto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> y actúa como el componente del objeto del documento para los elementos de proyecto y otros componentes de entorno implicados en la persistencia.  Para obtener más información, vea [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md).  
  
## En esta sección  
 [Cambiar la configuración de vista mediante la API heredada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Explica cómo cambiar la configuración de vista usando heredado API.  
  
 [Mediante el Administrador de texto para supervisar la configuración Global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explica cómo utilizar el administrador de texto para controlar la Configuración global.  
  
## Vea también  
 [Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)