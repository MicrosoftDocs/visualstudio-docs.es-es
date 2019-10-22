---
title: Agregar nuevos orígenes de datos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85c07ad7995bc614df4b988bb17fa8977452b5d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673059"
---
# <a name="add-new-data-sources"></a>Agregar nuevos orígenes de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el contexto de las herramientas de datos de .NET en Visual Studio, el término *origen de datos* hace referencia a los objetos de .net que se conectan a un almacén de datos y exponen los datos a una aplicación .net. Los diseñadores de Visual Studio pueden utilizar la salida del origen de datos para generar el código reutilizable que enlaza los datos a los formularios al arrastrar y colocar objetos de base de datos desde la ventana **orígenes de datos** . Este tipo de origen de datos puede ser:

- Una clase de un modelo de Entity Framework que está asociado a algún tipo de base de datos.

- Conjunto de datos que está asociado a algún tipo de base de datos.

- Una clase que representa un servicio de red como un servicio de datos Windows Communication Foundation (WCF) o un servicio REST.

- Una clase que representa un servicio de SharePoint.

- Una clase o colección de la solución.

> [!NOTE]
> Si no usa características de enlace de datos, conjuntos de datos, Entity Framework, LINQ to SQL, WCF o SharePoint, no se aplica el concepto de "origen de datos". Solo tiene que conectarse directamente a la base de datos mediante los objetos SQLCommand y comunicarse directamente con la base de datos.

 Los orígenes de datos se crean y editan mediante el **Asistente para la configuración de orígenes de datos** en una aplicación Windows Forms o Windows Presentation Foundation. Por Entity Framework, cree primero las clases de entidad y, a continuación, inicie el asistente seleccionando **proyecto**  > **Agregar nuevo origen de datos** (se describe con más detalle más adelante en este artículo).

 ![Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png "Asistente para configuración de orígenes de datos")

 Después de crear un origen de datos, este aparece en la ventana de herramientas **orígenes de datos** (Mayús + Alt + D o **Ver**  > **otras ventanas**  > **origen de datos**). Puede arrastrar un origen de datos desde la ventana **orígenes de datos** hasta una superficie de diseño de formulario o un control. Esto hace que se genere código reutilizable: código que muestra los datos que se originan en el almacén de datos para el usuario. En la ilustración siguiente se muestra un conjunto de elementos que se ha colocado en Windows Forms. Si seleccionó F5 en la aplicación, los datos de la base de datos subyacente aparecen en los controles del formulario.

 ![Operación de arrastre de origen de datos](../data-tools/media/raddata-data-source-drag-operation.png "raddata operación de arrastre de origen de datos")

## <a name="data-source-for-a-database-or-a-database-file"></a>Origen de datos de una base de datos o un archivo de base de datos

### <a name="dataset"></a>Conjunto de datos
 Para crear un conjunto de datos como un origen de datos, ejecute el **Asistente para configuración de orígenes de datos** (**proyecto**  > **Agregar nuevo** origen de datos) y elija el tipo de origen de datos de la **base** de datos. Siga las indicaciones para especificar una conexión de base de datos nueva o existente, o un archivo de base de datos.

### <a name="entity-classes"></a>Clases de entidad
 Para crear un modelo de Entity Framework como un origen de datos, ejecute primero el **Asistente para Entity Data Model** con el fin de crear las clases de entidad (**proyecto**  > **agregar nuevo elemento**  > **ADO.NET Entity Data Model**).

 ![Nuevo elemento de proyecto de modelo de Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata nuevo elemento de proyecto de modelo de Entity Framework")

 Elija el método por el que desea generar el modelo.

 ![Asistente para Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png "Asistente para Entity Data Model de raddata")

 Agregue el modelo como un origen de datos. Las clases que se generaron aparecen en el **Asistente para la configuración de orígenes de datos** al elegir la categoría **objetos** .

 ![Asistente para la configuración de orígenes de datos con clases de entidad](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata Asistente para la configuración de orígenes de datos con clases de entidad")

## <a name="data-source-for-a-service"></a>Origen de datos de un servicio
 Para crear un origen de datos a partir de un servicio de, ejecute el **Asistente para la configuración de orígenes de datos** y elija el tipo de origen de datos **servicio** . En realidad, es simplemente un acceso directo al cuadro de diálogo **Agregar referencia de servicio** , al que también se puede tener acceso haciendo clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccionando **Agregar referencia de servicio**.

 Cuando se crea un origen de datos desde un servicio, Visual Studio agrega una referencia de servicio al proyecto. Visual Studio también crea objetos proxy que corresponden a los objetos que devuelve el servicio. Por ejemplo, un servicio que devuelve un conjunto de DataSet se representa en el proyecto como un conjunto de DataSet; un servicio que devuelve un tipo específico se representa en el proyecto como el tipo devuelto.

 Puede crear un origen de datos a partir de los siguientes tipos de servicios:

- Data Services de WCF. Para obtener más información, vea [información general](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- Servicios de datos de WCF. Para obtener más información, vea [servicios de Windows Communication Foundation y WCF Data Services en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).

- Servicios Web.

    > [!NOTE]
    > Los elementos que aparecen en la ventana **orígenes de datos** dependen de los datos que devuelve el servicio. Algunos servicios podrían no proporcionar suficiente información para que el **Asistente para configuración de orígenes de datos** pueda crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, en la ventana orígenes de **datos** no aparecerá ningún elemento cuando se complete el asistente. Esto se debe a que los conjuntos de datos sin tipo no proporcionan un esquema y, por lo tanto, el asistente no tiene suficiente información para crear el origen de datos.

## <a name="data-source-for-an-object"></a>Origen de datos de un objeto
 Puede crear un origen de datos a partir de cualquier objeto que exponga una o varias propiedades públicas ejecutando el **Asistente para configuración de orígenes de datos** y, a continuación, seleccionando el tipo de origen de datos del **objeto** . Todas las propiedades públicas de un objeto se muestran en la ventana **orígenes de datos** .   Si usa Entity Framework y ha generado un modelo, aquí es donde encontrará las clases de entidad que serán los orígenes de datos de la aplicación.

 En la página **seleccionar los objetos de datos** , expanda los nodos de la vista de árbol para buscar los objetos a los que desea enlazar. La vista de árbol contiene nodos para el proyecto y para los ensamblados y otros proyectos a los que hace referencia el proyecto.

 Si desea enlazar a un objeto de un ensamblado o proyecto que no aparece en la vista de árbol, haga clic en **Agregar referencia** y use el **cuadro de diálogo Agregar referencia** para agregar una referencia al ensamblado o proyecto. Después de agregar la referencia, el ensamblado o proyecto se agrega a la vista de árbol.

> [!NOTE]
> Es posible que necesite compilar el proyecto que contiene los objetos antes de que los objetos aparezcan en la vista de árbol.

> [!NOTE]
> Para admitir el enlace de datos de arrastrar y colocar, los objetos que implementan la interfaz <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> deben tener un constructor predeterminado. De lo contrario, Visual Studio no puede crear una instancia del objeto de origen de datos y mostrará un error al arrastrar el elemento a la superficie de diseño.

## <a name="data-source-for-a-sharepoint-list"></a>Origen de datos para una lista de SharePoint
 Puede crear un origen de datos a partir de una lista de SharePoint ejecutando el **Asistente para la configuración de orígenes de datos** y seleccionando el tipo de origen de datos de **SharePoint** . SharePoint expone los datos a través de [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], por lo que la creación de un origen de datos de SharePoint es la misma que la creación de un origen de datos a partir de un servicio. Al seleccionar el elemento de **SharePoint** en el **Asistente para la configuración de orígenes de datos** , se abre el cuadro de diálogo **Agregar referencia de servicio** , donde se conecta al servicio de datos de SharePoint apuntando al servidor de SharePoint.  Esto requiere el SDK de SharePoint.

## <a name="see-also"></a>Vea también
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
