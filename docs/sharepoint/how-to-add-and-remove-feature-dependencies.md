---
title: Procedimiento Agregar y quitar dependencias de características | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 13fc731dcf5d96db569a969244b2375939afee62
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636975"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Filtrar Agregar y quitar dependencias de características
  La característica de SharePoint puede depender de otras características para la funcionalidad o datos. En estos casos, puede marcar estas otras características como dependencias para la característica. De este modo, el servidor de SharePoint asegura que se activan las características dependientes antes de que la característica está activada.

## <a name="add-dependencies"></a>Agregar dependencias
 Puede agregar otras características de la solución como dependencias. De este modo, puede asegurarse de que las características necesarias se instalan y se activa antes de instala la característica.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Para agregar una dependencia en una característica de la solución

1.  Abra el Diseñador de características, expanda el **dependencias de activación de característica** nodo y, a continuación, elija el **agregar** botón.

2.  En el **agregar dependencias de activación de característica** diálogo cuadro, elija el **agregar una dependencia en las características de la solución** botón de opción, elija el título de la característica que desea agregar como una dependencia y, a continuación, Elija la **agregar** botón.

     Puede agregar más de una característica eligiendo varios títulos durante la elección del **Ctrl** clave.

## <a name="addi-custom-dependencies"></a>Dependencias personalizadas de c
 Puede agregar las características que ya están implementadas en un servidor de SharePoint como una dependencia. De este modo, el proceso de activación de SharePoint que se comprueba para asegurarse de que se activan todas las características dependientes antes de instala la característica.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Para agregar una dependencia por el Id. de característica

1.  Abra el Diseñador de características, expanda el **dependencias de activación de característica** nodo y, a continuación, elija el **agregar** botón.

2.  En el **agregar dependencias de activación de característica** diálogo cuadro, elija el **agregar una dependencia personalizada** botón de opción.

3.  En el **Id. de característica** texto, escriba el GUID de la característica que desea marcar como una dependencia de activación y, a continuación, elija el **agregar** botón.

## <a name="edit-custom-dependencies"></a>Modificar las dependencias personalizadas
 Puede modificar dependencias personalizadas que agregó previamente. Sin embargo, las características dependientes que están en la solución solo se quita, no puede editar.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Para cambiar una dependencia en una característica de la solución

1.  Abra el Diseñador de características y, a continuación, expanda el **dependencias de activación de característica** nodo.

2.  Elija el nombre de la característica que desea editar y, a continuación, elija el **editar** botón.

3.  En el **Editar dependencia de activación de característica personalizada** cuadro de diálogo, cambie el título, el Id. de característica o la descripción y, a continuación, elija el **enviar** botón.

## <a name="remove-dependencies"></a>Quitar las dependencias

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Para quitar una dependencia en una característica de la solución

1.  En el Diseñador de características, expanda el **dependencias de activación de característica** nodo, elija el nombre de la característica que desea quitar y, a continuación, elija el **quitar** botón.

## <a name="see-also"></a>Vea también
- [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
