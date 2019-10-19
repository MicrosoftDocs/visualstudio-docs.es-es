---
title: Buscar y reemplazar, Entorno, Opciones (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.FindReplace
- VS.ToolsOptionsPages.Environment.FindandReplace
helpviewer_keywords:
- Find and Replace, Options dialog box
- Find and Replace, customizing
ms.assetid: f804d6d5-6309-46e4-8294-b83e880b5ec9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c17b25d8a837f751b8bd8ec108c0b821d58c6df0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657697"
---
# <a name="find-and-replace-environment-options-dialog-box"></a>Buscar y reemplazar, Entorno, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use esta página del cuadro de diálogo **Opciones** para controlar los cuadros de mensaje y otros aspectos de una operación de buscar y reemplazar. Puede tener acceso a este cuadro de diálogo desde el menú **Herramientas** haciendo clic en **Opciones**, expandiendo **Entorno** y, después, haciendo clic en **Buscar y reemplazar**. Si esta página no aparece en la lista, en el cuadro de diálogo **Opciones**, seleccione **Mostrar todas las configuraciones**.

> [!NOTE]
> Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="uielement-list"></a>Lista de UIElement
 **Mostrar mensajes informativos** Seleccione esta opción para mostrar todos los mensajes informativos de buscar y reemplazar que tengan la opción **Mostrar siempre este mensaje** . Por ejemplo, si ha elegido no mostrar el mensaje "La función Buscar ha llegado al punto de inicio de la búsqueda", al seleccionar esta opción provocaría que este mensaje informativo apareciera de nuevo cuando use Buscar y reemplazar.

 Si no quiere ver ningún mensaje informativo para Buscar y reemplazar, desactive esta opción.

 Cuando haya desactivado la opción **Mostrar siempre este mensaje** en algunos, pero no todos, los mensajes informativos de **Buscar y reemplazar**, la casilla **Mostrar mensajes informativos** aparece rellena pero no seleccionada. Para restaurar todos los mensajes de **Buscar y reemplazar** opcionales, desactive esta opción y, después, selecciónela de nuevo.

> [!NOTE]
> Esta opción no afecta a ningún mensaje informativo de **Buscar y reemplazar** que no muestre la opción **Mostrar siempre este mensaje**.

 **Mostrar mensajes de advertencia** Seleccione esta opción para mostrar todos los mensajes de búsqueda y reemplazo de precaución que tengan la opción **Mostrar siempre este mensaje** . Por ejemplo, si ha elegido no mostrar el mensaje de advertencia **Reemplazar todo** que aparece cuando intenta realizar reemplazos en archivos que no están abiertos en estos momentos para su edición, al seleccionar esta opción provocaría que este mensaje de advertencia aparezca de nuevo cuando intente Reemplazar todo.

 Si no quiere ver ningún mensaje de precaución para Buscar y reemplazar, desactive esta opción.

 Cuando haya desactivado la opción **Mostrar siempre este mensaje** en algunos, pero no todos, los mensajes de advertencia de **Buscar y reemplazar**, la casilla **Mostrar mensajes de advertencia** aparece rellena pero no seleccionada. Para restaurar todos los mensajes de **Buscar y reemplazar** opcionales, desactive esta opción y, después, selecciónela de nuevo.

> [!NOTE]
> Esta opción no afecta a ningún mensaje de advertencia de **Buscar y reemplazar** que no muestre la opción **Mostrar siempre este mensaje**.

 **Rellenar automáticamente el cuadro de diálogo Buscar con texto del editor** Seleccione esta opción para pegar el texto en cualquier lado del punto de inserción actual del editor en el campo **Buscar** cuando seleccione cualquier vista de la ventana **Buscar y reemplazar** desde el menú **Edición**. Desactive esta opción para usar el último patrón de búsqueda de la búsqueda anterior como la cadena **Buscar**.

## <a name="see-also"></a>Otras referencias
 [Buscar y reemplazar texto](../../ide/finding-and-replacing-text.md)
