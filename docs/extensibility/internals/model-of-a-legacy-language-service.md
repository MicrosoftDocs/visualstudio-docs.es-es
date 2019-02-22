---
title: Modelo de un servicio de lenguaje heredado | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a044d623931d024f15baba1532e3a563273242e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621947"
---
# <a name="model-of-a-legacy-language-service"></a>Modelo de un servicio de lenguaje heredado
Un servicio de lenguaje define los elementos y características para un idioma específico y se usa para proporcionar el editor con información específica de ese idioma. Por ejemplo, el editor debe saber los elementos y las palabras clave del lenguaje para admitir los colores de sintaxis.

 El servicio de lenguaje trabaja en estrecha colaboración con el búfer de texto administrado por el editor y la vista que contiene el editor. Microsoft IntelliSense **información rápida** opción es un ejemplo de una característica proporcionada por un servicio de lenguaje.

## <a name="a-minimal-language-service"></a>Un servicio de lenguaje mínimo
 El servicio de lenguaje más básico contiene los dos objetos siguientes:

- El *servicio de lenguaje* implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz. Un servicio de lenguaje tiene información sobre el lenguaje, como su nombre, las extensiones de nombre de archivo, el Administrador de ventanas de código y Coloreador.

- El *Coloreador* implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz.

  El siguiente dibujo conceptual muestra un modelo de un servicio de lenguaje básico.

  ![Gráfico del modelo de servicio de lenguaje](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") modelo de servicio de lenguaje básico

  Los hosts de la ventana de documento del *vista de documento* del editor, en este caso el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor básico. La vista del documento y el búfer de texto son propiedad del editor. Estos objetos funcionan con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a través de una ventana de documento especializado llama a un *ventana código*. La ventana de código se encuentra en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto que se crea y se controla mediante el IDE.

  Cuando se carga un archivo con una extensión específica, el editor localiza el servicio de lenguaje asociado a esa extensión y le pasa la ventana de código mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método. El servicio de lenguaje devuelve un *Administrador de ventanas de código*, que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaz.

  En la tabla siguiente proporciona información general de los objetos en el modelo.

| Componente | Object | Función |
|------------------| - | - |
| Búfer de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Una secuencia de texto de lectura/escritura de Unicode. Es posible para que utilice otras codificaciones de texto. |
| Ventana Código | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Una ventana de documento que contiene una o varias vistas de texto. Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está en modo de interfaz de múltiples documentos (MDI), la ventana de código es un formulario MDI secundario. |
| Vista de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Una ventana que permite al usuario navegar y ver el texto mediante el teclado y mouse (ratón). Aparece una vista de texto al usuario como un editor. Puede usar las vistas de texto en ventanas del editor normal, la ventana de salida y la ventana Inmediato. Además, puede configurar una o varias vistas de texto dentro de una ventana de código. |
| Administrador de texto | Administrado por el <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> de servicio, desde el cual obtener un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> puntero | Un componente que mantiene información común compartida por todos los componentes que se ha descrito anteriormente. |
| servicio de lenguaje | Implementación dependiente; implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Un objeto que proporciona el editor con información específica del idioma, como el resaltado de sintaxis, finalización de instrucciones y coincidencia de llaves. |

## <a name="see-also"></a>Vea también
- [Datos de documento y vista de documento en editores personalizados](../../extensibility/document-data-and-document-view-in-custom-editors.md)