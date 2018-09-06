---
title: Agregar nuevos orígenes de datos
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1bbe808f1c43e0f4083f5ed1d04db347560a2630
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35666636"
---
# <a name="add-new-data-sources"></a>Agregar nuevos orígenes de datos

En el contexto de las herramientas de datos de .NET en Visual Studio, el término *origen de datos* hace referencia a objetos de .NET que se conectan a un almacén de datos y exponen los datos a una aplicación. NET. Los diseñadores de Visual Studio pueden consumir la salida del origen de datos para generar el código reutilizable que enlaza los datos a los formularios al arrastrar y colocar los objetos de base de datos desde el **orígenes de datos** ventana. Este tipo de origen de datos puede ser:

- Una clase en un modelo de Entity Framework que está asociado a algún tipo de base de datos.

- Un conjunto de datos que está asociado a algún tipo de base de datos.

- Una clase que representa un servicio de red como un servicio de datos de Windows Communication Foundation (WCF) o un servicio REST.

- Una clase que representa un servicio de SharePoint.

- Una clase o una colección de la solución.

> [!NOTE]
> Si no usa características de enlace de datos, conjuntos de datos, Entity Framework, LINQ to SQL, WCF o SharePoint, el concepto de "data source" no es aplicable. Simplemente conéctese directamente a la base de datos mediante el uso de los objetos de SQLCommand y comunicarse directamente con la base de datos.

Crear y editar orígenes de datos mediante el **Asistente para configuración de origen de datos** en una aplicación Windows Forms o Windows Presentation Foundation. Para Entity Framework, primero cree las clases de entidad y, a continuación, inicie el asistente seleccionando **proyecto** > **Agregar nuevo origen de datos** (se describe con más detalle más adelante en este artículo).

![Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png)

Después de crear un origen de datos, aparece en el **orígenes de datos** ventana de herramientas (**MAYÚS**+**Alt**+**d.** o **vista** > **otros Windows** > **origen de datos**). Puede arrastrar un origen de datos desde el **orígenes de datos** ventana hasta una superficie de diseño del formulario o control. Esto hace que generar código reutilizable que muestra los datos del almacén de datos. La siguiente ilustración muestra un conjunto de datos que se ha quitado en un formulario de Windows. Si selecciona **F5** en la aplicación, los datos de la base de datos subyacente aparecen en los controles del formulario.

![Operación de arrastre del origen de datos](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Origen de datos para una base de datos o un archivo de base de datos

Puede crear un conjunto de datos o un modelo de Entity Framework para usarla como un origen de datos de una base de datos o un archivo de base de datos.

### <a name="dataset"></a>Conjunto de datos

Para crear un conjunto de datos como un origen de datos, ejecute el **Asistente para configuración de origen de datos** seleccionando **proyecto** > **Agregar nuevo origen de datos**. Elija la **base de datos** origen de datos escriba y siga las indicaciones para especificar una conexión de base de datos nueva o existente, o un archivo de base de datos.

### <a name="entity-classes"></a>Clases de entidad

Para crear un modelo de Entity Framework como un origen de datos:

1. Ejecute el **Asistente para Entity Data Model** para crear las clases de entidad. Seleccione **proyecto** > **Agregar nuevo elemento** > **ADO.NET Entity Data Model**.

   ![Nuevo elemento de proyecto de modelo de Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Elija el método que va a generar el modelo.

   ![Asistente para Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Agregar el modelo como un origen de datos. Las clases generadas aparecen en la **Asistente para configuración de origen de datos** cuando se elige el **objetos** categoría.

   ![Asistente para configuración de origen de datos con las clases de entidad](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Origen de datos para un servicio

Para crear un origen de datos de un servicio, ejecute el **Asistente para configuración de origen de datos** y elija el **servicio** tipo de origen de datos. Se trata de un acceso directo a la **Add Service Reference** cuadro de diálogo, que también puede acceder haciendo clic con el proyecto en **el Explorador de soluciones** y seleccionando **Agregar referencia de servicio**.

Cuando se crea un origen de datos de un servicio, Visual Studio agrega una referencia de servicio al proyecto. Visual Studio también crea objetos proxy que corresponden a los objetos que devuelve el servicio. Por ejemplo, un servicio que devuelve un conjunto de datos se representa en el proyecto como un conjunto de datos; un servicio que devuelve que un tipo específico se representa en el proyecto como el tipo devuelto.

Puede crear un origen de datos de los siguientes tipos de servicios:

- [Data Services de WCF](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Servicios de WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- servicios Web

    > [!NOTE]
    > Los elementos que aparecen en la **orígenes de datos** ventana dependen de los datos que devuelve el servicio. Algunos servicios podrían no proporcionar suficiente información para el **Asistente para configuración de origen de datos** para crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, no hay elementos aparecen en la **orígenes de datos** ventana cuando se complete el asistente. Esto es porque los datasets no escritos no proporcionan un esquema y, por lo tanto, el asistente no tiene información suficiente para crear el origen de datos.

## <a name="data-source-for-an-object"></a>Origen de datos para un objeto

Puede crear un origen de datos de cualquier objeto que expone una o más propiedades públicas ejecutando el **Asistente para configuración de origen de datos** y, a continuación, seleccionando la **objeto** tipo de origen de datos. Se muestran todas las propiedades públicas de un objeto en el **orígenes de datos** ventana. Si usa Entity Framework y ha generado un modelo, esto es donde encontrará las clases de entidad que son los orígenes de datos para la aplicación.

En el **seleccionar objetos de datos** , expanda los nodos en la vista de árbol para buscar los objetos que desea enlazar. La vista de árbol contiene nodos para el proyecto y para los ensamblados y otros proyectos que se hace referencia el proyecto.

Si desea enlazar a un objeto en un ensamblado o proyecto que no aparece en la vista de árbol, haga clic en **Agregar referencia** y usar el **Add Reference Dialog Box** para agregar una referencia al ensamblado o proyecto. Después de agregar la referencia, el ensamblado o proyecto se agrega a la vista de árbol.

> [!NOTE]
> Es posible que deba compilar el proyecto que contiene los objetos antes de que los objetos aparecen en la vista de árbol.

> [!NOTE]
> Para admitir el enlace de datos de arrastrar y colocar, los objetos que implementan la <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> interfaz debe tener un constructor predeterminado. En caso contrario, Visual Studio no puede crear instancias del objeto de origen de datos y muestra un error cuando se arrastra el elemento a la superficie de diseño.

## <a name="data-source-for-a-sharepoint-list"></a>Origen de datos para obtener una lista de SharePoint

Puede crear un origen de datos de una lista de SharePoint ejecutando el **Asistente para configuración de origen de datos** y seleccionando el **SharePoint** tipo de origen de datos. SharePoint expone los datos a través de WCF Data Services, por lo que crear un origen de datos de SharePoint es lo mismo que crear un origen de datos de un servicio. Seleccionar el **SharePoint** de elemento en el **Asistente para configuración de origen de datos** abre el **Add Service Reference** cuadro de diálogo, donde se conecta al servicio de datos de SharePoint señalando al servidor de SharePoint. Esto requiere el SDK de SharePoint.

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)