---
title: Información general sobre herramientas de diseño del modelo BDC | Microsoft Docs
description: Lea información general sobre las herramientas de diseño que se deben usar con un modelo de conectividad a datos profesionales (BDC). Obtenga información sobre el diseñador de BDC, la ventana detalles del método de BDC y el explorador de BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b398d9c00caf3a4fa2ca58bafa3273673a305859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851691"
---
# <a name="bdc-model-design-tools-overview"></a>Introducción a las herramientas de diseño del modelo BDC
  Puede diseñar un modelo de conectividad a datos profesionales (BDC) mediante el diseñador de BDC, la ventana **detalles del método de BDC** y el explorador de **BDC**.

 El **Explorador de BDC** permite examinar el modelo, buscar en el modelo y definir los descriptores de tipos.

## <a name="bdc-designer"></a>Diseñador de BDC
 El diseñador de BDC permite definir las entidades en el modelo y organizar visualmente sus relaciones entre sí. Use el diseñador de BDC para realizar las siguientes tareas:

- Agregar entidades al modelo.

- Quitar entidades del modelo.

- Definir relaciones entre entidades.

  Para abrir el diseñador de BDC, haga doble clic en el archivo de modelo del proyecto o abra el menú contextual del archivo de modelo y, a continuación, elija **abrir**. Agregue una entidad al modelo arrastrando o copiando una **entidad** desde el **cuadro de herramientas** hasta el diseñador. Para crear una asociación entre dos entidades, elija el control **Asociación** en el **cuadro de herramientas**, elija la primera entidad y, a continuación, elija la segunda entidad.

## <a name="bdc-method-details-window"></a>Ventana detalles del método de BDC
 Utilice la ventana **detalles del método de BDC** para definir los parámetros, las instancias y los descriptores de filtro de un método.

 Puede generar rápidamente el buscador, el buscador específico, el creador, el actualizador y los métodos de eliminación en la ventana **detalles del método de BDC** . Cuando se generan estos métodos, Visual Studio agrega metadatos, como los parámetros, las instancias y los descriptores de tipos, al método. Puede modificar estos metadatos para satisfacer su escenario específico.

 Para abrir la ventana **detalles del método de BDC** , en la barra de menús, elija **Ver**  >  **otros**  >  **detalles del método BDC** de Windows.

 Para ver los métodos en la ventana **detalles del método de BDC** , elija la entidad en el diseñador de BDC. Los métodos de la entidad seleccionada aparecen en la ventana **detalles del método de BDC** . Si no elige una entidad en el diseñador de BDC, la ventana **detalles del método de BDC** no muestra ninguna información.

 Expanda o contraiga los nodos en la ventana **detalles del método de BDC** para definir los parámetros, las instancias y los descriptores de filtro. Use el **Explorador de BDC** para definir los descriptores de tipo.

## <a name="bdc-explorer"></a>Explorador de BDC
 El **Explorador de BDC** muestra los elementos que componen el modelo. Para abrir el **Explorador de BDC**, en la barra de menús, elija **Ver**  >  **otro**  >  **Explorador de BDC** de Windows. Para examinar el modelo, expanda los nodos en el **Explorador de BDC**. Cada nodo representa un elemento en el XML del archivo de modelo.

 A medida que selecciona nodos en el **Explorador de BDC**, las propiedades de cada nodo que elija aparecen en la ventana **propiedades** . Muchas de estas propiedades corresponden a los atributos del archivo de modelo. Puede buscar en el modelo mediante el cuadro de búsqueda situado en la parte superior del **Explorador de BDC**.

> [!NOTE]
> El **Explorador de BDC** no muestra los identificadores, las propiedades personalizadas, las cadenas localizadas, los grupos de asociaciones, las acciones, los descriptores de filtro, las listas de control de acciones y los valores de parámetro predeterminados.

### <a name="define-type-descriptors"></a>Definir descriptores de tipos
 Use el **Explorador de BDC** para definir los descriptores de tipo. El explorador de BDC permite definir un descriptor de tipo una vez y, a continuación, volver a usar ese descriptor de tipos en otro lugar del modelo. Para ello, copie un descriptor de tipo y péguelo en cualquier otro parámetro o descriptor de tipo.

> [!NOTE]
> Los cambios en un descriptor de tipo original no afectan a las copias de ese descriptor de tipos.

 Para obtener más información, vea [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Vea también
- [Cómo: para crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md)
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)
- [Tutorial: crear una lista externa en SharePoint con datos económicos](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integración de datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
