---
title: Cuadro de diálogo Editor de colección de tipos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dae99166b8b811df75f2e2777d176e6778b60c7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670156"
---
# <a name="type-collection-editor-dialog-box"></a>Editor de colección de tipos (cuadro de diálogo)
El cuadro de diálogo Editor de la **colección de tipos** se usa para agregar tipos conocidos a las actividades de **envío** y **recepción** . Este cuadro de diálogo también se usa para agregar argumentos de tipo genérico a la actividad **InvokeMethod** . Cuando se usa para que las actividades de **envío** y **recepción** agreguen tipos conocidos, el cuadro de diálogo Editor de la **colección de tipos** requiere que las adiciones de tipo sean únicas. Si se agrega un tipo duplicado y se confirma el cambio haciendo clic en **Aceptar**, se devuelve un mensaje de error. Cuando se usa para que la actividad **InvokeMethod** agregue argumentos de tipo genérico, el cuadro de diálogo **Editor de colección de tipos** permite agregar tipos duplicados.

> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] sobre los tipos conocidos, vea [Data Contract Known Types](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).

 En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **colección de tipos** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Lista de tipos**|Una lista de los tipos que se han agregado o se han quitado.|

## <a name="to-bring-up-the-type-collection-editor"></a>Para mostrar el Editor de colección de tipos

#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Para mostrar el Editor de colección de tipos para las actividades Send y Receive

1. Seleccione la actividad de **envío** o **recepción** en la vista de diseño.

2. Presione **F4** para abrir la ventana **propiedades** .

3. En la ventana **propiedades** , haga clic en el botón de puntos suspensivos junto a la propiedad **KnownTypes** .

#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Para mostrar el Editor de colección de tipos para la actividad InvokeMethod

1. Seleccione la actividad **InvokeMethod** en la vista de diseño.

2. Presione **F4** para abrir la ventana **propiedades** .

3. En la ventana **propiedades** , haga clic en el botón de puntos suspensivos junto a la propiedad **GenericTypeArguments** .