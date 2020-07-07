---
title: 'Diseñador de paquetes: agregar & quitar características y elementos para empaquetar'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dfbda711c42e475af5f17c8799e53b13e26611a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014613"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Cómo: agregar y quitar características y elementos de un paquete mediante el diseñador de paquetes
  Al crear una solución de SharePoint, Visual Studio agrega las características predeterminadas de SharePoint al paquete en la solución. Antes de la implementación final, puede Agregar y quitar características y elementos de proyecto de SharePoint para modificar el paquete de SharePoint.

 Como alternativa, puede usar el explorador de empaquetado para agregar y quitar elementos de proyecto de SharePoint. También puede ver y cambiar la jerarquía de los elementos de proyecto de SharePoint y las características que se colocan en el paquete (. wsp). Para obtener más información, vea [Cómo: agregar y quitar características y elementos de un paquete mediante el explorador de empaquetado](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Agregar características a un paquete de SharePoint
 Puede usar el diseñador de paquetes para agregar características a un paquete de SharePoint.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Para agregar características de SharePoint con el diseñador de paquetes

1. Abra el **Diseñador de paquetes**.

    Para obtener más información, vea [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Agregue una o varias características de SharePoint realizando uno o varios de los pasos siguientes:

   1. Haga doble clic en cada elemento de los **elementos de la lista de soluciones** que desee agregar.

   2. Elija un elemento que desee agregar y, a continuación, elija el botón **Agregar** (>).

   3. Elija el botón **Agregar todo** (>>) para agregar todos los elementos a la vez.

      Por ejemplo, puede hacer doble clic en un elemento de los **elementos de** la lista de soluciones para agregarlo a los **elementos de la lista de paquetes** .

      Los elementos de proyecto y las características de SharePoint aparecen en los **elementos de la lista de paquetes** .

## <a name="remove-features-from-a-sharepoint-package"></a>Quitar características de un paquete de SharePoint
 Puede usar el diseñador de paquetes para quitar características de un paquete de SharePoint.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Para quitar características de SharePoint con el diseñador de paquetes

1. En la lista **elementos en el paquete** , elija un elemento que quiera quitar y, a continuación, elija el botón **quitar** (<) o elija el botón **quitar todo** (<<) para quitar todos los elementos.

     Los elementos de SharePoint aparecen en los **elementos de la lista de soluciones** .

## <a name="see-also"></a>Consulte también
- [Crear paquetes de soluciones de SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Cómo: crear un paquete](https://msdn.microsoft.com/b24be45c-e91d-49bb-afb0-7b265404214b)
