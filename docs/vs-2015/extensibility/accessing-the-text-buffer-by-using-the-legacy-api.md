---
title: Acceso al búfer de texto mediante la API heredada | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c52e4beb1397e9919c3bf670e009d7ca1060ce1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722191"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Acceso al búfer de texto mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El texto es responsable de administrar los flujos de texto y la persistencia de archivo. Aunque el búfer puede leer o escribir otros formatos, todas las comunicaciones normales con el búfer se realizan mediante el uso de Unicode. En las API heredadas, el búfer de texto puede utilizar uno - o un sistema de coordenadas bidimensional para identificar las ubicaciones de carácter en el búfer.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Dimensión de uno y dos sistemas de coordenadas  
 Unidimensional coordenadas de la posición se basan en la posición de un carácter desde el primer carácter en el búfer, por ejemplo, 147. Usa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaz para tener acceso a una ubicación unidimensional en el búfer. Un sistema de coordenadas bidimensional se basa en pares de línea y un índice. Por ejemplo, un carácter en el búfer 43, 5 podría estar en línea 43, cinco caracteres a la derecha del primer carácter en esa línea. Obtener acceso a una ubicación bidimensional en el búfer mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaz. Tanto el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> interfaces que implementa el objeto de búfer de texto (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) y puede tener acceso entre sí mediante el uso de `QueryInterface`. El diagrama siguiente muestra estas y otras interfaces de clave en <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Objeto de búfer de texto](../extensibility/media/vstextbuffer.gif "objeto vsTextBuffer")  
Objeto de búfer de texto  
  
 Aunque cualquier sistema de coordenadas funciona en el búfer de texto, está optimizado para usar coordenadas bidimensionales. Un sistema de coordenadas unidimensional puede crear una sobrecarga de rendimiento. Por lo tanto, use el sistema de coordenadas bidimensional siempre que sea posible.  
  
 La responsabilidad de segundo del búfer de texto es la persistencia de archivo. Para ello, se implementa el objeto de búfer de texto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> y actúa como el componente de objeto de datos de documentos para elementos de proyecto y otros componentes de entorno implicadas en la persistencia. Para obtener más información, consulte [abriendo y guardando elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cambio de la configuración de vista mediante la API heredada API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Explica cómo cambiar la configuración de vista mediante la API heredada.  
  
 [Uso del administrador de texto para supervisar la configuración global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explica cómo usar el Administrador de texto para supervisar la configuración global...  
  
## <a name="see-also"></a>Vea también  
 [Dentro del editor principal](../extensibility/inside-the-core-editor.md)

