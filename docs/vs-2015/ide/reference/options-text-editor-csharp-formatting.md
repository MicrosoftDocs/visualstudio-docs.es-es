---
title: Opciones, editor de texto, C#, formato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f75d2b73946a006057945b1e68f018a358e38279
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674198"
---
# <a name="options-text-editor-c-formatting"></a>Opciones, editor de texto, C#, formato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use el cuadro de diálogo de la página de propiedades **Formato** para establecer las opciones para proporcionar formato al código en el Editor de código. Para tener acceso a este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**, expanda **Editor de texto**, expanda **C#** y, después, haga clic en **Formato**.  
  
> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="general-settings"></a>Configuración general  
 La configuración general afecta a la manera en que el Editor de código aplica las opciones de formato al código.  
  
## <a name="uielement-list"></a>Lista de UIElement  
  
|Etiqueta|Descripción|  
|-----------|-----------------|  
|**Dar formato automáticamente a la instrucción completada al introducir ;**|Cuando está seleccionada, da formato a las instrucciones a su finalización según las opciones de formato seleccionadas para el Editor de código. Desactive esta casilla si no quiere que el Editor de código modifique las instrucciones.|  
|**Dar formato automáticamente al bloque completado al introducir }**|Cuando está seleccionada, da formato a los bloques de código según las opciones de formato seleccionadas para el Editor de código tan pronto como complete el bloque de código. Desactive esta casilla si no quiere que el Editor de código modifique los bloques.|  
|**Ajustar sangría al pegar**|Cuando está seleccionada, da formato al texto pegado en el Editor de código para que se adapte a las opciones de formato seleccionadas para el Editor de código. Desactive esta casilla si no quiere que se modifique el texto pegado.|  
  
## <a name="preview-window"></a>Ventana Vista previa  
 Los panales de opciones **Sangría**, **Nuevas líneas**, **Espaciado** y **Ajuste** muestran una ventana de vista previa. La ventana de vista previa muestra el efecto de cada opción. Para usar la ventana de vista previa, seleccione una opción de formato. La ventana de vista previa muestra un ejemplo de la opción seleccionada. Cuando cambia la configuración, por ejemplo, cuando activa o desactiva una casilla, la ventana de vista previa se actualiza para mostrar el efecto de la nueva configuración.  
  
## <a name="remarks"></a>Comentarios  
 Las opciones de sangría de las páginas **Pestañas** para cada idioma solo determinan dónde coloca el cursor el Editor de código cuando presiona ENTRAR al final de una línea. Las opciones de sangría en **Formato** se aplican cuando se aplica formato al código automáticamente, por ejemplo, cuando pega código en el archivo mientras la opción **Ajustar sangría al pegar** está seleccionada, y cuando el bloque al que se está dando formato se escribe manualmente.  
  
## <a name="see-also"></a>Vea también  
 [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
