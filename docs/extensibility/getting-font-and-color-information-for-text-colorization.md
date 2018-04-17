---
title: Obtener información de Color para los colores de texto y de fuente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c86e37d6d7da9da0a6b0978770bf7d7564fa19c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Obtención de fuente y la información de Color para el color de texto
El proceso que se representa o se muestra texto de los elementos de interfaz de usuario depende del tipo de las preferencias del proyecto, su tecnología y developer. El **fuentes y colores** página de propiedades almacena la configuración.

 Necesita la mayoría de las implementaciones que muestran texto los el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> y asociados de interfaces para la configuración de pantalla de presentación, recuperar y almacenar texto.

> [!NOTE]
>  Al personalizar el editor principal (que admite la **EditorCategory de texto**), se recomienda que utilice la tecnología de color en el servicio de lenguaje. Para obtener más información, consulte [información general de Color y fuente](../extensibility/font-and-color-overview.md).

## <a name="getting-default-font-and-color-information"></a>Obtener información de Color y fuente predeterminada
 Todas la **fuentes y colores** deben especificar los valores de las ventanas de mostrar texto en el **elementos para mostrar** de uno **categoría**. Para obtener más información, consulte [fuentes y colores, entorno, cuadro de diálogo Opciones](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Para colorear, un VSPackage debe obtener actual **fuentes y colores** configuración. Un VSPackage puede obtener la configuración actual de las formas siguientes, dependiendo de sus necesidades:

-   Usar el mecanismo de persistencia de fuente y color para recuperar el estado almacenado o actual. Para obtener más información, consulte [acceso a fuentes almacenados y la configuración de Color](../extensibility/accessing-stored-font-and-color-settings.md).

-   Use la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaz de un servicio que proporciona datos de fuente y color para obtener una instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, si el VSPackage no es también el proveedor de fuente y color.

-   Implementar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.

Para asegurarse de que los resultados obtenidos mediante sondeo están actualizadas, puede ser útil usar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si se necesita una actualización antes de llamar a los métodos de recuperación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.

Después de ha obtenido información de fuente y color, analice el texto que se mostrará para identificar elementos que requieren la coloración. Muestra el texto en la ventana con las fuentes adecuadas y los colores.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Utilizar fuentes y texto](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Trabajar con colores](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (interfaz de dispositivo gráfico)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)