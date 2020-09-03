---
title: 'Extensión de Excel de muestra: ActionFilter (Clase) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c286f25159f3ee1934a27d2242e97482f7ec424
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672179"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Extensión de Excel de muestra: ActionFilter (Clase)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta clase interna extiende la clase [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) y representa un filtro para las acciones de prueba en un [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] elemento.

## <a name="simple-properties"></a>Propiedades simples
 Estas propiedades de solo lectura permiten al programador especificar cómo el marco de pruebas de IU codificadas va a ejecutar este filtro de acción de prueba. Por ejemplo, la propiedad `UITestActionFilter.Name` proporciona el nombre del filtro de acción. Otras propiedades obtienen `UITestActionFilter.Category` del filtro de acción, `UITestActionFilter.FilterType` y el nombre `UITestActionFilter.Group` para las acciones de prueba que se filtran mediante este filtro de acción de prueba. Otras indican si `UITestActionFilter.ApplyTimeout` y también si la acción de prueba es `UITestActionFilter.Enabled`.

## <a name="processrule-method"></a>Método ProcessRule
 Este método se llama mediante el marco de prueba de IU codificada y ejecuta el filtro en el `IUITestActionStack` proporcionado. Esta invalidación determinada quita una acción de elección de mouse en una celda cuando la siguiente acción en la pila envía pulsaciones de tecla a la celda. Después, devuelve `false`.

## <a name="private-methods"></a>Métodos privados
 El método `IsLeftClick` determina si la acción proporcionada representa un clic del mouse. El método `AreActionsOnSameExcelCell` determina si dos acciones proporcionadas que se ejecutan en la misma celda en Excel.

## <a name="see-also"></a>Consulte también

- [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
