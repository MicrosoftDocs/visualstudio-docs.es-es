---
title: Cuadro de diálogo Editor de la colección de tipos de Diseñador de flujo de trabajo
description: Obtenga información sobre cómo puede usar el cuadro de diálogo Editor de colección de tipos para agregar tipos conocidos a las actividades de envío y recepción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8f194ee792f2a60df71a78af6f41e45aaac91da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875268"
---
# <a name="type-collection-editor-dialog-box"></a>Editor de colección de tipos (cuadro de diálogo)

El cuadro de diálogo Editor de la **colección de tipos** se usa para agregar tipos conocidos a las actividades de **envío** y **recepción** . Este cuadro de diálogo también se usa para agregar argumentos de tipo genérico a la actividad **InvokeMethod** . Cuando se usa para que las actividades de **envío** y **recepción** agreguen tipos conocidos, el cuadro de diálogo Editor de la **colección de tipos** requiere que las adiciones de tipo sean únicas. Si se agrega un tipo duplicado y se confirma el cambio haciendo clic en **Aceptar**, se devuelve un mensaje de error. Cuando se usa para que la actividad **InvokeMethod** agregue argumentos de tipo genérico, el cuadro de diálogo **Editor de colección de tipos** permite agregar tipos duplicados.

Para obtener más información, vea [tipos conocidos de contratos de datos](/dotnet/framework/wcf/feature-details/data-contract-known-types).

En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **colección de tipos** .

|Elemento de UI|Descripción|
|-|-----------------|
|**Type List**|Una lista de los tipos que se han agregado o se han quitado.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Para mostrar el Editor de colección de tipos para las actividades Send y Receive

1. Seleccione la actividad de **envío** o **recepción** en la vista de diseño.

2. Presione **F4** para abrir la ventana **propiedades** .

3. En la ventana **propiedades** , haga clic en el botón de puntos suspensivos junto a la propiedad **KnownTypes** .

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Para mostrar el Editor de colección de tipos para la actividad InvokeMethod

1. Seleccione la actividad **InvokeMethod** en la vista de diseño.

2. Presione **F4** para abrir la ventana **propiedades** .

3. En la ventana **propiedades** , haga clic en el botón de puntos suspensivos junto a la propiedad **GenericTypeArguments** .
