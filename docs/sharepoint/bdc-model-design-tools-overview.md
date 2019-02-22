---
title: Información general de las herramientas de diseño del modelo BDC | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb2f257feaa8faa6acf58c8e8763d15d08a1079e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596573"
---
# <a name="bdc-model-design-tools-overview"></a>Introducción a las herramientas de diseño de modelo BDC
  Puede diseñar un modelo de conectividad de datos profesionales (BDC) mediante el Diseñador de BDC, el **detalles del método de BDC** ventana y el **Explorador de BDC**.

 El **Explorador de BDC** le permite examinar el modelo, buscar en el modelo y definir los descriptores de tipo.

## <a name="bdc-designer"></a>Diseñador de BDC
 El Diseñador de BDC le permite definir las entidades en el modelo y organizar visualmente sus relaciones entre sí. Use el Diseñador de BDC para realizar las tareas siguientes:

- Agregar entidades al modelo.

- Quitar las entidades del modelo.

- Definir relaciones entre entidades.

  Para abrir el Diseñador de BDC, haga doble clic en el archivo de modelo en el proyecto, o abra el menú contextual para el archivo de modelo y, a continuación, elija **abrir**. Agregar una entidad al modelo arrastrando o copiando una **entidad** desde el **cuadro de herramientas** hasta el diseñador. Para crear una asociación entre dos entidades, elija el **asociación** en controlar la **cuadro de herramientas**, elija la primera entidad y, a continuación, elija la segunda entidad.

## <a name="bdc-method-details-window"></a>Ventana Detalles del método de BDC
 Use la **detalles del método de BDC** ventana para definir los parámetros, las instancias y descriptores de filtro de un método.

 Puede generar rápidamente métodos Finder, buscador específico, Creator, Updater y Deleter en el **detalles del método de BDC** ventana. Cuando se generan estos métodos, Visual Studio agrega los metadatos, como parámetros, las instancias y descriptores de tipo para el método. Puede modificar estos metadatos para satisfacer su escenario concreto.

 Para abrir el **detalles del método de BDC** ventana, en la barra de menús, elija **vista** > **Other Windows** > **detalles del método de BDC** .

 Para ver los métodos en el **detalles del método de BDC** ventana, seleccione la entidad en el Diseñador de BDC. Los métodos de la entidad seleccionada aparecen en la **detalles del método de BDC** ventana. Si no elige una entidad en el Diseñador de BDC, el **detalles del método de BDC** ventana no muestra ninguna información.

 Expandir o contraer nodos en el **detalles del método de BDC** ventana para definir parámetros, las instancias y descriptores de filtro. Use la **Explorador de BDC** para definir descriptores de tipo.

## <a name="bdc-explorer"></a>Explorador de BDC
 El **Explorador de BDC** muestra los elementos que conforman el modelo. Para abrir el **Explorador de BDC**, en la barra de menús, elija **vista** > **Other Windows** > **Explorador de BDC**. Para examinar el modelo, expanda los nodos en el **Explorador de BDC**. Cada nodo representa un elemento en el XML del archivo del modelo.

 Mientras selecciona los nodos en el **Explorador de BDC**, aparecen las propiedades de cada nodo que elija en la **propiedades** ventana. Muchas de estas propiedades corresponden a atributos en el archivo de modelo. Puede buscar el modelo mediante el cuadro de búsqueda en la parte superior de la **Explorador de BDC**.

> [!NOTE]
>  El **Explorador de BDC** no muestra los identificadores, propiedades personalizadas, cadenas localizadas, grupos de asociaciones, acciones, descriptores de filtro, listas de control de acción y los valores de parámetro predeterminados.

### <a name="define-type-descriptors"></a>Definir descriptores de tipo
 Use la **Explorador de BDC** para definir descriptores de tipo. El Explorador de BDC le permite definir un descriptor de tipo una vez y, a continuación, volver a usar ese descriptor de tipo en otro lugar en el modelo. Para lograr esto, copie un descriptor de tipos y péguelo en cualquier otro parámetro o descriptor de tipos.

> [!NOTE]
>  Los cambios realizados en un descriptor de tipos original no afectan a las copias de ese descriptor de tipos.

 Para obtener más información, vea [Cómo: Definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Vea también
- [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)
- [Tutorial: Crear una lista externa en SharePoint con datos profesionales](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Creación de un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Diseñar un modelo de conectividad de datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
