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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301210"
---
# <a name="add-new-data-sources"></a>Agregar nuevos orígenes de datos

En el contexto de las herramientas de datos de .NET en Visual Studio, el término origen de *datos* hace referencia a objetos .NET que se conectan a un almacén de datos y ponen los datos a disposición de una aplicación .NET. Los diseñadores de Visual Studio pueden consumir la salida del origen de datos para generar el código reutilizable que enlaza los datos a formularios al arrastrar y colocar objetos de base de datos desde la ventana Orígenes de **datos.** Este tipo de origen de datos puede ser:

- Una clase en un modelo de Entity Framework que está asociado a algún tipo de base de datos.

- Conjunto de datos asociado a algún tipo de base de datos.

- Clase que representa un servicio de red como un servicio de datos de Windows Communication Foundation (WCF) o un servicio REST.

- Clase que representa un servicio de SharePoint.

- Una clase o colección en la solución.

> [!NOTE]
> Si no usa características de enlace de datos, conjuntos de datos, Entity Framework, LINQ to SQLLINQ to SQL, WCF o SharePoint, no se aplica el concepto de un "origen de datos". Simplemente conéctese directamente a la base de datos mediante el uso de la SQLCommand objetos y comunicarse directamente con la base de datos.

Crear y editar orígenes de datos mediante el **Asistente para configuración** de orígenes de datos en una aplicación de Windows Forms o Windows Presentation Foundation. Para Entity Framework, primero cree las clases de entidad y, a continuación, inicie el asistente seleccionando **Agregar proyecto** > **nuevo origen** de datos (descrito con más detalle más adelante en este artículo).

![Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Ventana de orígenes de datos

Después de crear un origen de datos, aparece en la ventana de herramientas **Orígenes** de datos.

> [!TIP]
> Para abrir la ventana **Orígenes** de datos, asegúrese de que el proyecto está abierto y, a continuación, presione **Mayús**+**Alt**+**D** o elija **Ver** > otros orígenes de**datos**de**Windows** > .

Puede arrastrar un origen de datos desde la ventana **Orígenes** de datos a una superficie o control de diseño de formulario. Esto hace que se genere código reutilizable que muestra los datos del almacén de datos.

En la siguiente ilustración se muestra un conjunto de datos que se ha colocado en un formulario Windows. Si selecciona **F5** en la aplicación, los datos de la base de datos subyacente aparecen en los controles del formulario.

![Operación de arrastre del origen de datos](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Origen de datos para una base de datos o un archivo de base de datos

Puede crear un conjunto de datos o un modelo de Entity Framework para usarlo como origen de datos para una base de datos o un archivo de base de datos.

### <a name="dataset"></a>Dataset

Para crear un conjunto de datos como origen de datos, ejecute el **Asistente para configuración** del origen de datos seleccionando Agregar **proyecto** > **nuevo origen**de datos . Elija el tipo de origen de datos **de** base de datos y siga las instrucciones para especificar una conexión de base de datos nueva o existente, o un archivo de base de datos.

### <a name="entity-classes"></a>Clases de entidad

Para crear un modelo de Entity Framework como origen de datos:

1. Ejecute el **Asistente para Entity Data Model** para crear las clases de entidad. Seleccione **Agregar** > **proyecto nuevo elemento** > **ADO.NET Entity Data Model**.

   ![Nuevo elemento de proyecto de modelo de Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Elija el método por el que desea generar el modelo.

   ![Asistente para Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Agregue el modelo como origen de datos. Las clases generadas aparecen en el **Asistente para configuración** del origen de datos al elegir la categoría **Objetos.**

   ![Asistente de configuración de orígenes de datos con clases de entidad](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Origen de datos para un servicio

Para crear un origen de datos a partir de un servicio, ejecute el **Asistente para configuración** del origen de datos y elija el tipo de origen de datos de **servicio.** Esto es solo un acceso directo al cuadro de diálogo Agregar referencia de **servicio,** al que también puede tener acceso haciendo clic con el botón derecho en el proyecto en el **Explorador** de soluciones y seleccionando **Agregar referencia**de servicio .

Al crear un origen de datos a partir de un servicio, Visual Studio agrega una referencia de servicio al proyecto. Visual Studio también crea objetos proxy que corresponden a los objetos que devuelve el servicio. Por ejemplo, un servicio que devuelve un conjunto de datos se representa en el proyecto como un conjunto de datos; un servicio que devuelve un tipo específico se representa en el proyecto como el tipo devuelto.

Puede crear un origen de datos a partir de los siguientes tipos de servicios:

- [Servicios de datos de Microsoft WCF](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Servicios WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- SERVICIOS WEB

    > [!NOTE]
    > Los elementos que aparecen en la ventana **Orígenes** de datos dependen de los datos que devuelve el servicio. Algunos servicios podrían no proporcionar suficiente información para que el **Asistente para configuración de orígenes de datos** pueda crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, no aparecerá ningún elemento en la ventana **Orígenes** de datos al completar el asistente. Esto se debe a que los conjuntos de datos sin tipo no proporcionan un esquema y, por lo tanto, el asistente no tiene suficiente información para crear el origen de datos.

## <a name="data-source-for-an-object"></a>Origen de datos para un objeto

Puede crear un origen de datos a partir de cualquier objeto que exponga una o varias propiedades públicas ejecutando el **Asistente para configuración** del origen de datos y, a continuación, seleccionando el tipo de origen de datos **Objeto.** Todas las propiedades públicas de un objeto se muestran en la ventana **Orígenes de datos.** Si usa Entity Framework y ha generado un modelo, aquí es donde encontrará las clases de entidad que son los orígenes de datos de la aplicación.

En la página **Seleccionar los objetos** de datos, expanda los nodos de la vista de árbol para buscar los objetos a los que desea enlazar. La vista de árbol contiene nodos para el proyecto y para ensamblados y otros proyectos a los que hace referencia el proyecto.

Si desea enlazar a un objeto de un ensamblado o proyecto que no aparece en la vista de árbol, haga clic en **Agregar referencia** y use el cuadro de diálogo **Agregar referencia** para agregar una referencia al ensamblado o proyecto. Después de agregar la referencia, el ensamblaje o proyecto se agrega a la vista de árbol.

> [!NOTE]
> Es posible que deba compilar el proyecto que contiene los objetos antes de que los objetos aparezcan en la vista de árbol.

> [!NOTE]
> Para admitir el enlace de datos de <xref:System.ComponentModel.ITypedList> arrastrar <xref:System.ComponentModel.IListSource> y colocar, los objetos que implementan la interfaz o deben tener un constructor predeterminado. De lo contrario, Visual Studio no puede crear instancias del objeto de origen de datos y muestra un error al arrastrar el elemento a la superficie de diseño.

## <a name="data-source-for-a-sharepoint-list"></a>Origen de datos para una lista de SharePoint

Puede crear un origen de datos a partir de una lista de SharePoint ejecutando el **Asistente para configuración** del origen de datos y seleccionando el tipo de origen de datos de **SharePoint.** SharePoint expone datos a través de Servicios de datos de WCFWCF Data Services, por lo que crear un origen de datos de SharePoint es lo mismo que crear un origen de datos a partir de un servicio. Al seleccionar el elemento de **SharePoint** en el **Asistente para** configuración del origen de datos, se abre el cuadro de diálogo Agregar referencia de **servicio,** donde se conecta al servicio de datos de SharePoint apuntando al servidor de SharePoint. Esto requiere el SDK de SharePoint.

## <a name="see-also"></a>Consulte también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
