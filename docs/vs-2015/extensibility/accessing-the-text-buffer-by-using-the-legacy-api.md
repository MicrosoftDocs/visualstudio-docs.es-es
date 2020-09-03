---
title: Acceso al búfer de texto mediante la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184999"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Acceso al búfer de texto mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El texto es responsable de administrar las secuencias de texto y la persistencia de los archivos. Aunque el búfer puede leer o escribir otros formatos, toda la comunicación normal con el búfer se realiza mediante Unicode. En las API heredadas, el búfer de texto puede usar un sistema de coordenadas de una o dos dimensiones para identificar ubicaciones de caracteres en el búfer.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Sistemas de coordenadas de una y dos dimensiones  
 Una posición de coordenadas unidimensional se basa en la posición de un carácter del primer carácter del búfer, como 147. La interfaz se utiliza <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> para tener acceso a una ubicación unidimensional en el búfer. Un sistema de coordenadas bidimensional se basa en pares de línea y de índice. Por ejemplo, un carácter del búfer en 43, 5 sería en la línea 43, cinco caracteres a la derecha del primer carácter de la línea. Puede tener acceso a una ubicación bidimensional en el búfer mediante la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaz. El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> objeto de búfer de texto () implementa las interfaces y, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> y se puede tener acceso a ellas entre sí mediante el uso de `QueryInterface` . En el diagrama siguiente se muestran estas y otras interfaces clave en <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![Objeto de búfer de texto](../extensibility/media/vstextbuffer.gif "Objeto vstextbuffer")  
Objeto de búfer de texto  
  
 Aunque cualquier sistema de coordenadas funciona en el búfer de texto, está optimizado para utilizar coordenadas bidimensionales. Un sistema de coordenadas unidimensional puede crear una sobrecarga de rendimiento. Por lo tanto, utilice el sistema de coordenadas bidimensional siempre que sea posible.  
  
 La segunda responsabilidad del búfer de texto es la persistencia de archivos. Para ello, el objeto de búfer de texto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> y actúa como el componente de objeto de datos de documento para los elementos de proyecto y otros componentes de entorno implicados en la persistencia. Para obtener más información, vea [abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cambio de la configuración de vista mediante la API heredada API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Explica cómo cambiar la configuración de la vista mediante la API heredada.  
  
 [Uso del administrador de texto para supervisar la configuración global](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Explica cómo usar el administrador de texto para supervisar la configuración global.  
  
## <a name="see-also"></a>Consulte también  
 [Dentro del editor principal](../extensibility/inside-the-core-editor.md)
