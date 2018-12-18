---
title: 'Diseñador de flujo de trabajo: cuadro de diálogo Editor de la colección de tipo'
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08c6e8e2f7851d74bfbeb0399dd758ae0ca25b4f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812768"
---
# <a name="type-collection-editor-dialog-box"></a>Editor de colección de tipos (cuadro de diálogo)

El **Editor de la colección de tipo** cuadro de diálogo se usa para agregar tipos conocidos para la **enviar** y **recepción** actividades. Este cuadro de diálogo también se usa para agregar argumentos de tipo genérico para el **InvokeMethod** actividad. Cuando se usa para la **enviar** y **recepción** actividades para agregar tipos conocidos, el **Editor de la colección de tipo** cuadro de diálogo requiere que se agreguen tipos únicos. Si se agrega un tipo duplicado y se confirma el cambio haciendo **Aceptar**, se devuelve un mensaje de error. Cuando se usa para la **InvokeMethod** actividad para agregar argumentos de tipo genérico, la **Editor de la colección de tipo** cuadro de diálogo permite la adición de tipos duplicados.

Para obtener más información, consulte [tipos conocidos de contratos de datos](/dotnet/framework/wcf/feature-details/data-contract-known-types).

La tabla siguiente describen los elementos de interfaz de usuario de la **tipo colección** cuadro de diálogo.

|Elemento de la interfaz de usuario|Descripción|
|-|-----------------|
|**Lista de tipos**|Una lista de los tipos que se han agregado o se han quitado.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Para mostrar el Editor de colección de tipos para las actividades Send y Receive

1.  Seleccione el **enviar** o **recepción** actividad en la vista Diseño.

2.  Presione **F4** para que aparezca el **propiedades** ventana.

3.  En el **propiedades** ventana, haga clic en el botón de puntos suspensivos situado junto a la **KnownTypes** propiedad.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Para mostrar el Editor de colección de tipos para la actividad InvokeMethod

1.  Seleccione el **InvokeMethod** actividad en la vista Diseño.

2.  Presione **F4** para que aparezca el **propiedades** ventana.

3.  En el **propiedades** ventana, haga clic en el botón de puntos suspensivos situado junto a la **GenericTypeArguments** propiedad.