---
title: "Cuadro de diálogo Editor de la colección de tipo | Documentos de Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f873ef2f2f30e307c7f9ec16a612eb76d09633c9
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="type-collection-editor-dialog-box"></a>Editor de colección de tipos (cuadro de diálogo)

El **Editor de la colección de tipo** cuadro de diálogo se usa para agregar tipos conocidos a la **enviar** y **recepción** actividades. Este cuadro de diálogo también se utiliza para agregar argumentos de tipo genérico a la **InvokeMethod** actividad. Cuando se utiliza para la **enviar** y **recepción** actividades para agregar tipos conocidos, la **Editor de la colección de tipo** cuadro de diálogo requiere las adiciones de tipo sean únicos. Si se agrega un tipo duplicado y se confirma el cambio haciendo clic en **Aceptar**, se devuelve un mensaje de error. Cuando se utiliza para la **InvokeMethod** actividad para agregar argumentos de tipo genérico, la **Editor de la colección de tipo** cuadro de diálogo permite que se agreguen tipos duplicados.

Para obtener más información, consulte [tipos conocidos de contrato de datos](/dotnet/framework/wcf/feature-details/data-contract-known-types).

La tabla siguiente describen los elementos de interfaz de usuario de la **tipo de colección** cuadro de diálogo.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Lista de tipos**|Una lista de los tipos que se han agregado o se han quitado.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Para mostrar el Editor de colección de tipos para las actividades Send y Receive

1.  Seleccione el **enviar** o **recepción** actividad en la vista Diseño.

2.  Presione **F4** para que aparezca el **propiedades** ventana.

3.  En el **propiedades** (ventana), haga clic en el botón de puntos suspensivos situado junto a la **KnownTypes** propiedad.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Para mostrar el Editor de colección de tipos para la actividad InvokeMethod

1.  Seleccione el **InvokeMethod** actividad en la vista Diseño.

2.  Presione **F4** para que aparezca el **propiedades** ventana.

3.  En el **propiedades** (ventana), haga clic en el botón de puntos suspensivos situado junto a la **GenericTypeArguments** propiedad.