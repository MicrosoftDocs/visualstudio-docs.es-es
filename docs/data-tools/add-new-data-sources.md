---
title: Agregar nuevos orígenes de datos
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 555d32eb295e944060d2efe0b843e9d157b7c675
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408563"
---
# <a name="add-new-data-sources"></a>Agregar nuevos orígenes de datos

En el contexto de las herramientas de datos de .NET en Visual Studio, el término *origen de datos* hace referencia a los objetos de .net que se conectan a un almacén de datos y hacen que los datos estén disponibles para una aplicación .net. Los diseñadores de Visual Studio pueden utilizar la salida del origen de datos para generar el código reutilizable que enlaza los datos a los formularios al arrastrar y colocar objetos de base de datos desde la ventana **orígenes de datos** . Este tipo de origen de datos puede ser:

- Una clase de un modelo de Entity Framework que está asociado a algún tipo de base de datos.

- Conjunto de datos que está asociado a algún tipo de base de datos.

- Una clase que representa un servicio de red como un servicio de datos Windows Communication Foundation (WCF) o un servicio REST.

- Una clase que representa un servicio de SharePoint.

- Una clase o colección de la solución.

> [!NOTE]
> Si no está utilizando características de enlace de datos, conjuntos de datos, Entity Framework, LINQ to SQL, WCF o SharePoint, no se aplica el concepto de "origen de datos". Solo tiene que conectarse directamente a la base de datos mediante los objetos SQLCommand y comunicarse directamente con la base de datos.

Los orígenes de datos se crean y editan mediante el **Asistente para la configuración de orígenes de datos** en una aplicación Windows Forms o Windows Presentation Foundation. Por Entity Framework, cree primero las clases de entidad y, a continuación, inicie el asistente seleccionando **proyecto** > **Agregar nuevo origen de datos** (se describe con más detalle más adelante en este artículo).

![Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Ventana de orígenes de datos

Después de crear un origen de datos, este aparece en la ventana de herramientas **orígenes de datos** .

> [!TIP]
> Para abrir la **ventana orígenes de datos** , asegúrese de que el proyecto está abierto y, a continuación, presione **mayús**+**Alt**+**D** o elija **Ver** > **otras ventanas** > **orígenes de datos**.

Puede arrastrar un origen de datos desde la ventana **orígenes de datos** hasta una superficie de diseño de formulario o un control. Esto hace que se genere código reutilizable que muestra los datos del almacén de datos.

En la ilustración siguiente se muestra un conjunto de elementos que se ha colocado en Windows Forms. Si selecciona **F5** en la aplicación, los datos de la base de datos subyacente aparecen en los controles del formulario.

![Operación de arrastre de origen de datos](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Origen de datos de una base de datos o un archivo de base de datos

Puede crear un conjunto de datos o un modelo de Entity Framework para usarlo como origen de datos para un archivo de base de datos o de base de datos.

### <a name="dataset"></a>Dataset

Para crear un conjunto de datos como un origen de datos, ejecute el **Asistente para la configuración de orígenes de datos** seleccionando **proyecto** > **Agregar nuevo origen de datos**. Elija el tipo de origen de datos Data-Source y siga las indicaciones para especificar una conexión de base de datos nueva o existente, o un archivo de base **de datos.**

### <a name="entity-classes"></a>Clases de entidad

Para crear un modelo de Entity Framework como un origen de datos:

1. Ejecute el **Asistente para Entity Data Model** para crear las clases de entidad. Seleccione **proyecto** > **agregar nuevo elemento** > **ADO.NET Entity Data Model**.

   ![Nuevo elemento de proyecto de modelo de Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Elija el método por el que desea generar el modelo.

   ![Asistente para Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Agregue el modelo como un origen de datos. Las clases generadas aparecen en el **Asistente para la configuración de orígenes de datos** cuando se elige la categoría **objetos** .

   ![Asistente para la configuración de orígenes de datos con clases de entidad](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Origen de datos de un servicio

Para crear un origen de datos a partir de un servicio de, ejecute el **Asistente para la configuración de orígenes de datos** y elija el tipo de origen de datos **servicio** . Esto es simplemente un acceso directo al cuadro de diálogo **Agregar referencia de servicio** , al que también se puede tener acceso haciendo clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccionando **Agregar referencia de servicio**.

Cuando se crea un origen de datos desde un servicio, Visual Studio agrega una referencia de servicio al proyecto. Visual Studio también crea objetos proxy que corresponden a los objetos que devuelve el servicio. Por ejemplo, un servicio que devuelve un conjunto de DataSet se representa en el proyecto como un conjunto de DataSet; un servicio que devuelve un tipo específico se representa en el proyecto como el tipo devuelto.

Puede crear un origen de datos a partir de los siguientes tipos de servicios:

- [Servicios de datos de WCF](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Servicios WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- SERVICIOS WEB

    > [!NOTE]
    > Los elementos que aparecen en la ventana **orígenes de datos** dependen de los datos que devuelve el servicio. Algunos servicios podrían no proporcionar suficiente información para que el **Asistente para configuración de orígenes de datos** pueda crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, en la ventana **orígenes de datos** no aparece ningún elemento cuando se completa el asistente. Esto se debe a que los conjuntos de datos sin tipo no proporcionan un esquema y, por lo tanto, el asistente no tiene suficiente información para crear el origen de datos.

## <a name="data-source-for-an-object"></a>Origen de datos de un objeto

Puede crear un origen de datos a partir de cualquier objeto que exponga una o varias propiedades públicas ejecutando el **Asistente para configuración de orígenes de datos** y, a continuación, seleccionando el tipo de origen de datos del **objeto** . Todas las propiedades públicas de un objeto se muestran en la ventana **orígenes de datos** . Si usa Entity Framework y ha generado un modelo, aquí es donde encontrará las clases de entidad que son los orígenes de datos de la aplicación.

En la página **seleccionar los objetos de datos** , expanda los nodos de la vista de árbol para buscar los objetos a los que desea enlazar. La vista de árbol contiene nodos para el proyecto y para los ensamblados y otros proyectos a los que hace referencia el proyecto.

Si desea enlazar a un objeto de un ensamblado o proyecto que no aparece en la vista de árbol, haga clic en **Agregar referencia** y use el **cuadro de diálogo Agregar referencia** para agregar una referencia al ensamblado o proyecto. Después de agregar la referencia, el ensamblado o proyecto se agrega a la vista de árbol.

> [!NOTE]
> Es posible que necesite compilar el proyecto que contiene los objetos antes de que los objetos aparezcan en la vista de árbol.

> [!NOTE]
> Para admitir el enlace de datos de arrastrar y colocar, los objetos que implementan la interfaz <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> deben tener un constructor predeterminado. De lo contrario, Visual Studio no puede crear una instancia del objeto de origen de datos y muestra un error al arrastrar el elemento a la superficie de diseño.

## <a name="data-source-for-a-sharepoint-list"></a>Origen de datos para una lista de SharePoint

Puede crear un origen de datos a partir de una lista de SharePoint ejecutando el **Asistente para la configuración de orígenes de datos** y seleccionando el tipo de origen de datos de **SharePoint** . SharePoint expone los datos a través de WCF Data Services, por lo que la creación de un origen de datos de SharePoint es la misma que la creación de un origen de datos a partir de un servicio. Al seleccionar el elemento de **SharePoint** en el **Asistente para la configuración de orígenes de datos** , se abre el cuadro de diálogo **Agregar referencia de servicio** , donde se conecta al servicio de datos de SharePoint apuntando al servidor de SharePoint. Esto requiere el SDK de SharePoint.

## <a name="see-also"></a>Consulte también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
