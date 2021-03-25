---
title: Modelo de un servicio de lenguaje heredado | Microsoft Docs
description: Use este modelo de un servicio de lenguaje mínimo para el editor principal de Visual Studio como guía para crear su propio servicio de lenguaje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 216bfaf9400847c265820e4bb5967fd3c992caa7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063231"
---
# <a name="model-of-a-legacy-language-service"></a>Modelo de un servicio de lenguaje heredado
Un servicio de lenguaje define los elementos y las características de un lenguaje específico y se usa para proporcionar al editor información específica de ese idioma. Por ejemplo, el editor necesita conocer los elementos y las palabras clave del lenguaje con el fin de admitir el color de la sintaxis.

 El servicio de lenguaje funciona estrechamente con el búfer de texto administrado por el editor y la vista que contiene el editor. La opción **información rápida** de Microsoft IntelliSense es un ejemplo de una característica proporcionada por un servicio de lenguaje.

## <a name="a-minimal-language-service"></a>Un servicio de lenguaje mínimo
 El servicio de lenguaje más básico contiene los dos objetos siguientes:

- El *servicio de lenguaje* implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz. Un servicio de lenguaje tiene información sobre el lenguaje, incluidos el nombre, las extensiones de nombre de archivo, el administrador de la ventana de código y el coloreador.

- El *coloreador* implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz.

  El siguiente dibujo conceptual muestra un modelo de un servicio de lenguaje básico.

  ![Gráfico de modelo de servicio de lenguaje](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Modelo de servicio de lenguaje básico

  La ventana de documento hospeda la *vista de documento* del editor, en este caso, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Editor básico. La vista de documento y el búfer de texto son propiedad del editor. Estos objetos funcionan con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a través de una ventana de documento especializada denominada *ventana de código*. La ventana de código se encuentra en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto creado y controlado por el IDE.

  Cuando se carga un archivo con una extensión determinada, el editor busca el servicio de lenguaje asociado a esa extensión y lo pasa a la ventana de código llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método. El servicio de lenguaje devuelve un *Administrador de ventanas de código*, que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaz.

  En la tabla siguiente se proporciona información general sobre los objetos del modelo.

| Componente | Object | Función |
|------------------| - | - |
| Búfer de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Secuencia de texto de lectura/escritura Unicode. El texto puede usar otras codificaciones. |
| Ventana de código | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Ventana de documento que contiene una o más vistas de texto. Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está en modo de interfaz de múltiples documentos (MDI), la ventana de código es un elemento secundario de MDI. |
| Vista de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Ventana que permite al usuario navegar y ver texto mediante el teclado y el mouse. Aparece una vista de texto para el usuario como editor. Puede usar vistas de texto en ventanas de editor normales, en la ventana de salida y en la ventana inmediato. Además, puede configurar una o varias vistas de texto dentro de una ventana de código. |
| Administrador de texto | Administrado por el <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> servicio, desde el que obtiene un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> puntero. | Componente que mantiene la información común compartida por todos los componentes descritos anteriormente. |
| Servicio de lenguaje | Dependiente de la implementación; implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Objeto que proporciona al editor información específica del lenguaje, como el resaltado de sintaxis, la finalización de instrucciones y la coincidencia de llaves. |

## <a name="see-also"></a>Consulte también
- [Datos de documento y vista de documento en editores personalizados](../../extensibility/document-data-and-document-view-in-custom-editors.md)
