---
title: Modelo de un servicio de lenguaje heredado (Legacy Language Service) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707047"
---
# <a name="model-of-a-legacy-language-service"></a>Modelo de un servicio de lenguaje heredado
Un servicio de lenguaje define los elementos y características de un idioma específico y se usa para proporcionar al editor información específica de ese idioma. Por ejemplo, el editor necesita conocer los elementos y palabras clave del lenguaje para admitir el color de sintaxis.

 El servicio de lenguaje funciona estrechamente con el búfer de texto administrado por el editor y la vista que contiene el editor. La opción **Información rápida** de Microsoft IntelliSense es un ejemplo de una característica proporcionada por un servicio de lenguaje.

## <a name="a-minimal-language-service"></a>Un servicio de lenguaje mínimo
 El servicio de lenguaje más básico contiene los dos objetos siguientes:

- El *servicio de* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> lenguaje implementa la interfaz. Un servicio de lenguaje tiene información sobre el idioma, incluido su nombre, extensiones de nombre de archivo, administrador de ventanas de código y colorante.

- El *colorante* implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> la interfaz.

  El siguiente dibujo conceptual muestra un modelo de un servicio de lenguaje básico.

  ![Gráfico del modelo de servicio de lenguaje](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Modelo básico de servicio de idiomas

  La ventana del documento aloja la *vista* de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documento del editor, en este caso el editor principal. La vista de documento y el búfer de texto son propiedad del editor. Estos objetos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funcionan a través de una ventana de documento especializada denominada ventana de *código*. La ventana de código <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> está contenida en un objeto creado y controlado por el IDE.

  Cuando se carga un archivo con una extensión determinada, el editor busca el servicio de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> asociado a esa extensión y le pasa la ventana de código llamando al método. El servicio de lenguaje devuelve un administrador <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> de ventanas de *código,* que implementa la interfaz.

  En la tabla siguiente se proporciona una visión general de los objetos del modelo.

| Componente | Object | Función |
|------------------| - | - |
| Búfer de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Una secuencia de texto de lectura/escritura Unicode. Es posible que el texto utilice otras codificaciones. |
| Ventana de código | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Ventana de documento que contiene una o varias vistas de texto. Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está en modo de interfaz de varios documentos (MDI), la ventana de código es un elemento secundario MDI. |
| Vista de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Una ventana que permite al usuario navegar y ver texto con el teclado y el ratón. Una vista de texto aparece al usuario como editor. Puede utilizar vistas de texto en las ventanas normales del editor, la ventana Salida y la ventana Inmediato. Además, puede configurar una o varias vistas de texto dentro de una ventana de código. |
| Administrador de texto | Gestionado por <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> el servicio, del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> que se obtiene un puntero | Componente que mantiene información común compartida por todos los componentes descritos anteriormente. |
| Servicio de idiomas | Depende de la implementación; Implementa<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Objeto que proporciona al editor información específica del lenguaje, como resaltado de sintaxis, finalización de instrucciones y coincidencia de llaves. |

## <a name="see-also"></a>Vea también
- [Datos de documento y vista de documento en editores personalizados](../../extensibility/document-data-and-document-view-in-custom-editors.md)
