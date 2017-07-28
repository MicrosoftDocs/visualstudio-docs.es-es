---
title: Opciones, editor de texto, C#, IntelliSense | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 25
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: b34b280b3558003c5c3ad92515d773bc7d45fdda
ms.contentlocale: es-es
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-c-intellisense"></a>Opciones, editor de texto, C#, IntelliSense
Use la página de propiedades **IntelliSense** para modificar la configuración que afecta al comportamiento de IntelliSense para Visual C#. Puede tener acceso a la página de propiedades **IntelliSense** haciendo clic en **Opciones** en el menú **Herramientas**, después hacer clic en **C#** en la carpeta **Editor de texto** y, después, hacer clic en **IntelliSense.**  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 La página de propiedades **IntelliSense** contiene las siguientes propiedades:  
  
## <a name="completion-lists"></a>Listas de finalización  
 **Mostrar lista de completado después de escribir un carácter**  
 Cuando esta opción está seleccionada, IntelliSense muestra automáticamente la lista de finalización cuando comienza a escribir. Cuando esta opción no está seleccionada, la finalización de IntelliSense todavía está disponible desde el menú **IntelliSense** o presionando CTRL+BARRA ESPACIADORA.  
  
 **Palabras clave de lenguaje en listas de finalización**  
 Cuando esta opción está seleccionada, IntelliSense agrega palabras clave de C#, por ejemplo, [class](/dotnet/csharp/language-reference/keywords/class), a la lista de finalización.  
  
 **Colocar fragmentos de código en las listas de finalización**  
 Cuando esta opción está seleccionada, IntelliSense agrega alias para los fragmentos de código de C# a la lista de finalización. En el caso en que el alias de fragmento de código sea el mismo que una palabra clave, por ejemplo, [class](/dotnet/csharp/language-reference/keywords/class), la palabra clave se reemplaza mediante el acceso directo. Para obtener más información, vea [Fragmentos de código de Visual C#](../../ide/visual-csharp-code-snippets.md).  
  
## <a name="selection-in-completion-lists"></a>Selección en las listas de finalización  
 **Confirmado escribiendo los siguientes caracteres:**  
 Especifica todos los caracteres que ejecutan la finalización automática de IntelliSense para el elemento seleccionado en la lista de finalización, después de que se escriban.  
  
 **Confirmado presionando la barra espaciadora**  
 Especifica que se incluya la acción de presionar la barra espaciadora para ejecutar la finalización automática de IntelliSense para el elemento seleccionado en la lista de finalización.  
  
 **Agregar nueva línea con Entrar al final de palabras completas**  
 Especifica que si escribe todos los caracteres para una entrada en la lista de finalización y, después, presiona ENTRAR, se crea una nueva línea automáticamente y el cursor se mueve a la nueva línea.  
  
 Por ejemplo, si escribe `else` y, después, presiona ENTRAR, aparece lo siguiente en el editor:  
  
 `else`  
  
 `|` (ubicación del cursor)  
  
 En cambio, si escribe solo `el` y, después, presiona ENTRAR, aparece lo siguiente en el editor:  
  
 `else|` (ubicación del cursor)  
  
## <a name="intellisense-member-selection"></a>Selección de miembros de IntelliSense  
 **Preselecciona el miembro usado recientemente**  
 Cuando esta opción está seleccionada, IntelliSense preselecciona los miembros que ha seleccionado recientemente en el cuadro Lista de miembros emergente para la finalización automática del nombre de objeto, durante su sesión actual en el entorno de desarrollo integrado (IDE). El historial de los miembros usados recientemente se borra entre cada sesión del IDE. Para obtener más información, vea [IntelliSense para los miembros usados más recientemente](../../ide/visual-csharp-intellisense.md#most-recently-used-members).  
  
## <a name="see-also"></a>Vea también  
 [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)   
 [Comentarios de documentación XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Usar IntelliSense](../../ide/using-intellisense.md)
