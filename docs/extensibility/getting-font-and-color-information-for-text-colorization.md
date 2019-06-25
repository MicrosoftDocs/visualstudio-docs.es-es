---
title: Obtención de información de fuente y Color para la coloración de texto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b35e52effe9a261eeb159ca9460e4351ae5f658
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342499"
---
# <a name="get-font-and-color-information-for-text-colorization"></a>Obtener información de fuente y color de coloración de texto
El proceso que se representa o muestra el texto con colores de elementos de interfaz de usuario depende del tipo de proyecto, su tecnología y desarrollador de preferencias. El **fuentes y colores** página de propiedades almacena la configuración.

 La mayoría de las implementaciones que muestran texto con colores necesita el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> y asociados de interfaces para la configuración de pantalla de presentación, recuperar y almacenar texto.

> [!NOTE]
> Al personalizar el editor básico (que admite el **texto EditorCategory**), se recomienda que use la tecnología de color en el servicio de lenguaje. Para obtener más información, consulte [información general de fuente y color](../extensibility/font-and-color-overview.md).

## <a name="get-default-font-and-color-information"></a>Obtener información de fuente y color predeterminado
 Todas las **fuentes y colores** se debe especificar la configuración de las ventanas de mostrar texto en el **elementos para mostrar** de uno **categoría**. Para obtener más información, consulte [fuentes y colores, entorno, cuadro de diálogo Opciones](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Para colorear, un VSPackage debe obtener actual **fuentes y colores** configuración. Un VSPackage puede obtener la configuración actual de las maneras siguientes, según sus necesidades:

- Utilice el mecanismo de persistencia de fuente y color para recuperar el estado actual o almacenado. Para obtener más información, consulte [acceso a la configuración de fuente y color almacenada](../extensibility/accessing-stored-font-and-color-settings.md).

- Use la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaz de un servicio que proporciona datos de fuente y color para obtener una instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>si VSPackage no es también el proveedor de fuente y color.

- Implementar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.

Para asegurarse de que los resultados obtenidos mediante sondeo están actualizadas, puede ser útil usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si se necesita una actualización antes de llamar a los métodos de recuperación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.

Después de haber obtenido la información de fuente y color, analizar el texto que se mostrará para identificar los elementos que requieren la coloración. Mostrar el texto en la ventana con las fuentes adecuadas y los colores.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Utilizar las fuentes y texto](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Trabajar con colores](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (interfaz de dispositivo gráfico)](https://msdn.microsoft.com/library/7e1d4540-bb2e-4257-8eee-eee376acba83)