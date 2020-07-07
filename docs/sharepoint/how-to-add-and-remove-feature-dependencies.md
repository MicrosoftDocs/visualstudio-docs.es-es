---
title: 'Cómo: agregar y quitar dependencias de características | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c318a7dc4672a10e993d0149ec77e7f94679d465
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014781"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Cómo: agregar y quitar dependencias de características
  La característica de SharePoint puede depender de otras características para la funcionalidad o los datos. En estos casos, puede marcar estas otras características como dependencias de la característica. De este modo, el servidor de SharePoint garantiza que las características dependientes se activan antes de que se active la característica.

## <a name="add-dependencies"></a>Adición de dependencias
 Puede agregar otras características de la solución como dependencias. De este modo, puede asegurarse de que las características necesarias están instaladas y activadas antes de que se instale la característica.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Para agregar una dependencia en una característica de la solución

1. Abra el diseñador de características, expanda el nodo **dependencias de activación de características** y, a continuación, elija el botón **Agregar** .

2. En el cuadro de diálogo **Agregar dependencias de activación de características** , elija el botón de opción **Agregar una dependencia en las características en la solución** , elija el título de la característica que desea agregar como dependencia y, a continuación, elija el botón **Agregar** .

     Puede agregar más de una característica eligiendo varios títulos mientras elige la tecla **Ctrl** .

## <a name="addi-custom-dependencies"></a>Dependencias personalizadas de Addi
 Puede agregar características que ya están implementadas en un servidor de SharePoint como una dependencia. De este modo, el proceso de activación de SharePoint comprueba para asegurarse de que todas las características dependientes se activan antes de que se instale la característica.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Para agregar una dependencia por el ID. de característica

1. Abra el diseñador de características, expanda el nodo **dependencias de activación de características** y, a continuación, elija el botón **Agregar** .

2. En el cuadro de diálogo **Agregar dependencias de activación de características** , elija el botón de opción **Agregar una dependencia personalizada** .

3. En el cuadro de texto ID. de **característica** , escriba el GUID de la característica que desea marcar como una dependencia de activación y, a continuación, elija el botón **Agregar** .

## <a name="edit-custom-dependencies"></a>Editar dependencias personalizadas
 Puede editar las dependencias personalizadas que agregó anteriormente. Sin embargo, las características dependientes que se encuentran en la solución solo se pueden quitar, no editar.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Para cambiar una dependencia de una característica de la solución

1. Abra el diseñador de características y, a continuación, expanda el nodo **dependencias de activación de características** .

2. Elija el nombre de la característica que desea editar y, a continuación, elija el botón **Editar** .

3. En el cuadro de diálogo **Editar dependencia de activación de característica personalizada** , cambie el título, el identificador de característica o la descripción y, a continuación, elija el botón **Enviar** .

## <a name="remove-dependencies"></a>Eliminación de dependencias

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Para quitar una dependencia de una característica de la solución

1. En el diseñador de características, expanda el nodo **dependencias de activación de características** , elija el nombre de la característica que desea quitar y, a continuación, elija el botón **quitar** .

## <a name="see-also"></a>Consulte también
- [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Cómo: agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
