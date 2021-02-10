---
title: Diseñar un modelo de conectividad a datos profesionales | Microsoft Docs
description: Diseñar un modelo de conectividad a datos profesionales (BDC). Agregar entidades y métodos. Definir parámetros de método. Agregar descriptores de filtro. Valide el modelo BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fb1aa194688533855b7c5bd1d58a4e3b97ac749
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948848"
---
# <a name="design-a-business-data-connectivity-model"></a>Diseño de un modelo de conectividad a datos profesionales
  Puede desarrollar un modelo para el servicio de conectividad a datos profesionales (BDC) agregando entidades y métodos a un archivo de modelo. Una entidad describe una colección de campos de datos. Por ejemplo, una entidad puede representar una tabla de una base de datos. Un método realiza una tarea como agregar, eliminar o actualizar los datos representados por las entidades. Para obtener más información, vea [integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>agregar entidades
 Puede Agregar una entidad arrastrando o copiando una **entidad** desde el **cuadro de herramientas** de Visual Studio hasta el diseñador de BDC. Para obtener más información, vea [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Defina los campos de la entidad en una clase. Por ejemplo, puede Agregar un campo denominado `Address` a una `Customer` clase. Puede Agregar una nueva clase al proyecto o utilizar una clase existente creada con otras herramientas, como el Object Relational Designer (Object Relational Designer). El nombre de la entidad y el nombre de la clase que representa la entidad no tienen que coincidir. La clase se relaciona con la entidad al definir los métodos en el modelo.

## <a name="add-methods"></a>Agregar métodos
 El servicio BDC llama a los métodos del modelo cuando los usuarios ven, agregan, actualizan o eliminan información en una lista o elemento Web basado en el modelo. Debe agregar un método al modelo para cada tarea que el usuario pueda realizar. Cree métodos seleccionando cualquiera de los cinco tipos de método básicos de la ventana **detalles del método de BDC** . En la tabla siguiente se describen los cinco métodos básicos de un modelo BDC.

|Método|Descripción|
|------------|-----------------|
|Selector|Devuelve una colección de instancias de entidad. Se llama cuando el usuario abre la lista o el elemento Web. Para obtener más información, consulte [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md).|
|método Finder específico|Devuelve una instancia de entidad específica. Se llama cuando un usuario ve los detalles de un elemento específico en una lista. Para obtener más información, vea [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Creador|Agrega nuevos datos al origen de datos de una entidad. Se llama cuando los usuarios eligen el botón **nuevo elemento** de la cinta de opciones de una lista basada en el modelo. Para obtener más información, consulte [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md).|
|Updater|Modifica los datos de una lista. Se llama cuando los usuarios actualizan información en una lista. Para obtener más información, vea [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md).|
|Deleter|Quita los datos. Se le llama cuando los usuarios eliminan un elemento de la lista. Para obtener más información, consulte [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Definir parámetros de método
 Al crear un método, Visual Studio agrega los parámetros de entrada y salida adecuados para el tipo de método. Estos parámetros son simplemente marcadores de posición. En la mayoría de los casos, debe modificar los parámetros para que pasen o devuelvan el tipo de datos correcto. Por ejemplo, de forma predeterminada, un método Finder devuelve una cadena. En la mayoría de los casos, desea modificar el parámetro devuelto del método Finder para que devuelva una colección de entidades. Puede hacerlo modificando el descriptor de tipo del parámetro. Un descriptor de tipo es una colección de atributos que describe el tipo de datos de un parámetro. Para obtener más información, vea [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio permite copiar descriptores de tipo entre los parámetros del modelo. Por ejemplo, podría definir un descriptor de tipo denominado `CustomerTD` para el parámetro devuelto del `GetCustomer` método. Puede copiar el `CustomerTD` descriptor de tipos en el **Explorador de BDC** y, a continuación, pegar el descriptor de tipos en el parámetro de entrada del `CreateCustomer` método. Esto evita tener que definir el mismo descriptor de tipo más de una vez.

## <a name="method-instances"></a>Instancias de método
 Cuando se crea un método, Visual Studio agrega una instancia de método predeterminada. Una instancia de método es una referencia a un método, además de los valores predeterminados de los parámetros. Un único método puede tener varias instancias de método. Cada instancia es una combinación de la firma del método y un conjunto de valores predeterminados. Para obtener más información, vea [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Al ejecutar el proyecto, las instancias de método aparecen en una lista desplegable encima de la lista de SharePoint. Los usuarios pueden elegir instancias de método para ver los datos.

 Para agregar valores predeterminados a la instancia del método, debe modificar directamente el XML del modelo. Para obtener más información, consulte [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Agregar descriptores de filtro
 Es posible que los consumidores del modelo deseen recuperar instancias de una entidad que coincidan con algunos criterios. Para habilitar esta funcionalidad, puede Agregar un descriptor de filtro a un método. Los descriptores de filtro permiten a los consumidores del modelo filtrar los conjuntos de resultados del método pasando valores a los métodos antes de que se ejecuten. Para obtener más información, consulte [Cómo: agregar parámetros de filtro a operaciones para limitar las instancias del sistema externo](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 SharePoint proporciona varias características que permiten a los usuarios proporcionar valores de filtro. Por ejemplo, los datos empresariales elementos web proporcionan un cuadro de texto de filtro. Los usuarios pueden limitar los datos de una lista escribiendo un valor en el cuadro de texto. Para obtener más información sobre cómo agregar un descriptor de filtro a un método, vea [Cómo: agregar un descriptor de filtro a un método Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Propiedades de descriptor de filtro
 Debe establecer el valor de las propiedades del **descriptor de tipo**, **nombre** y **tipo** asociados de un descriptor de filtro. Todas las demás propiedades son opcionales.

 La propiedad del **descriptor de tipos asociada** relaciona el descriptor de filtro con un parámetro de entrada. Cuando un usuario proporciona un valor de filtro, el servicio BDC pasa ese valor al método mediante el parámetro de entrada.

 La propiedad **Type** describe el patrón de filtrado que quiere usar. En SharePoint, el patrón de filtrado que seleccione afecta al texto que aparece en la interfaz de usuario (UI). Por ejemplo, para un patrón de filtrado de comparador, el texto **es igual que** aparece como un control sobre un elemento Web de datos económicos. Para obtener más información acerca de cada patrón de filtrado, consulte [tipos de filtros admitidos por el BDC](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

 Para obtener más información acerca de las propiedades de un descriptor de filtro, vea [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Proporcionar valores predeterminados
 En algunos casos, es posible que el usuario no proporcione un valor de filtro. Puede proporcionar un valor predeterminado agregando un valor predeterminado a la instancia del método o estableciendo el valor predeterminado en el código del método. Para obtener más información sobre cómo agregar un valor predeterminado a la instancia de método, vea [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Para obtener un ejemplo de cómo establecer el valor predeterminado de un parámetro de entrada en el código del método, consulte [Cómo: agregar un descriptor de filtro a un método de buscador](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Validación del modelo
 Puede validar el modelo durante el desarrollo. Visual Studio identifica los problemas que pueden impedir que el modelo se comporte según lo esperado. Estos problemas aparecen en el **lista de errores** de Visual Studio.

 Para validar un modelo, abra el menú contextual del diseñador de BDC y, a continuación, elija **validar**. Si el modelo contiene errores, aparecen en el **lista de errores**. Puede trasladar rápidamente el cursor al código que contiene un error si hace doble clic en el error en la lista. Como alternativa, puede elegir repetidamente las teclas **F8** o **MAYÚS** + **F8** para ir hacia delante o hacia atrás por los errores de la lista.

 Se pueden producir errores de validación cuando se infringen de alguna manera las reglas del modelo. Por ejemplo, si la propiedad **IsCollection** de un descriptor de tipo está establecida en **true**, pero no existe ningún descriptor de tipo secundario, aparecerá un error de validación. Es posible que tenga que hacer referencia a las reglas de un modelo BDC para comprender algunos errores que aparecen en la **lista de errores** de Visual Studio. Para obtener más información sobre las reglas de un modelo BDC, vea [BDCMetadata Schema](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Depurar la solución que contiene el modelo
 Puede depurar el código como si se depurara cualquier código en Visual Studio. Para depurar el código, establezca puntos de interrupción en cualquier parte del código y, a continuación, inicie el depurador. Visual Studio abre el sitio de SharePoint. En SharePoint, cree una lista o un elemento Web que use los datos empresariales. A continuación, puede recorrer el código. Para obtener más información sobre la depuración de proyectos de SharePoint, vea [Solución de problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

 También puede depurar el código de los ensamblados personalizados que agregue al proyecto. Sin embargo, para depurar el código en un ensamblado personalizado, debe agregar el ensamblado al paquete de solución. Para obtener más información, consulte [Cómo: agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Para obtener más información sobre cómo agregar un ensamblado personalizado al proyecto, vea [Cómo: incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).

### <a name="configure-bdc-security"></a>Configuración de la seguridad de BDC
 Es posible que tenga que modificar la configuración de seguridad en SharePoint antes de poder depurar la solución. Para modificar esta configuración, abra la aplicación de servicio de conectividad a datos profesionales en el sitio web de administración central de SharePoint 2010. En el cuadro de diálogo **establecer permisos de almacén de metadatos** , agregue su cuenta de usuario y, a continuación, seleccione cualquiera de las siguientes opciones:

|Tarea|Opción|
|----------|------------|
|Para implementar modelos en el servicio BDC.|Editar|
|Para crear listas y elementos web mediante el uso de tipos de contenido externo (entidades) en el modelo.|Seleccionable en clientes|
|Para crear, leer, actualizar y eliminar datos de entidad.|Execute|

 Para obtener más información acerca de esta configuración, vea [Administración del servicio de conectividad a datos profesionales](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14)).

 También puede establecer permisos de seguridad para modelos individuales o tipos de contenido externo. Para obtener más información sobre cómo establecer los permisos de seguridad de un modelo, vea [Administración de modelos de BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)). Para obtener más información sobre cómo establecer los permisos de seguridad de un tipo de contenido externo, vea [Administración de tipos de contenido externo](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14)).

> [!NOTE]
> Use esta configuración para depurar una solución en el servidor de SharePoint local. Para obtener más información sobre cómo configurar las opciones de seguridad relacionadas con BDC en el servidor de SharePoint de producción, consulte [información general de seguridad de servicios de conectividad de datos profesionales](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14)).

### <a name="retract-models-that-become-corrupt"></a>Retirar los modelos que están dañados
 La primera vez que se inicia el depurador, Visual Studio implementa todo el modelo en SharePoint. En cada momento, Visual Studio actualiza el modelo en SharePoint con los cambios que realice entre las implementaciones.

 Puede haber situaciones en las que desee que Visual Studio Retire completamente el modelo de SharePoint. Por ejemplo, un modelo puede resultar dañado.  Para volver a implementar el modelo en SharePoint, establezca la propiedad **actualización incremental** del modelo en **false** y, a continuación, inicie el depurador. La propiedad **actualización incremental** aparece en la ventana **propiedades** cuando se selecciona el nodo que representa el modelo en el **Explorador de BDC**. De forma predeterminada, el nombre del modelo es **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Cambiar los nombres de identificador de entidades en el modelo
 Si cambia el nombre de un identificador después de implementar el modelo, es posible que reciba un error de implementación. No se puede resolver este error si se establece la propiedad **actualización incremental** del modelo en **false**. Debe retirar el modelo manualmente y, a continuación, volver a implementar la solución. Para obtener más información, vea [solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). Puede evitar este error si establece la propiedad **actualización incremental** en **false** antes de implementar inicialmente el modelo.

## <a name="locate-documentation-for-bdc-model-elements"></a>Buscar la documentación de los elementos del modelo BDC
 Visual Studio agrega un elemento XML al modelo para cada entidad, método u otro elemento que cree. Los atributos de elemento aparecen como propiedades en la ventana **propiedades** . Para obtener información sobre los elementos y atributos que Visual Studio genera al diseñar el modelo, vea [BDCMetadata Schema](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)|Describe las herramientas que puede usar para diseñar visualmente un modelo para el BDC.|
|[Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)|Muestra cómo agregar tipos de contenido externo, o entidades, al modelo.|
|[Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)|Muestra cómo agregar un método que permite a los usuarios ver una lista de entidades de una lista o un elemento Web.|
|[Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)|Muestra cómo agregar un método que permite a los usuarios ver los detalles de una entidad específica.|
|[Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)|Muestra cómo agregar un método que permite a los usuarios agregar registros a un origen de datos directamente desde una lista o un elemento Web.|
|[Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md)|Muestra cómo agregar un método que permite a los usuarios quitar datos de un origen de datos mediante las opciones de la interfaz de usuario (UI) de una lista o un elemento Web.|
|[Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)|Muestra cómo agregar un método que permite a los usuarios cambiar los registros de datos de un origen de datos directamente desde una lista o un elemento Web.|
|[Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Muestra cómo usar la ventana detalles del método en Visual Studio para agregar parámetros de entrada y de devolución a un método.|
|[Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Muestra cómo definir los tipos de datos de parámetros en el modelo.|
|[Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)|Muestra cómo crear una instancia de un método que el BDC ejecuta.|
|[Cómo: agregar un descriptor de filtro a un método Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Muestra cómo permitir a los usuarios limitar el número de instancias devueltas por un método de buscador.|
|[Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)|Describe cómo se pueden definir las relaciones entre las entidades del modelo. Los datos empresariales elementos web, las listas externas y las aplicaciones personalizadas pueden mostrar estas relaciones de datos en una interfaz de usuario (UI).|
|[Cómo: crear una asociación entre entidades](../sharepoint/how-to-create-an-association-between-entities.md)|Muestra cómo definir las relaciones entre las entidades del modelo.|
|[Tutorial: creación de la lista externa en SharePoint con datos económicos](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Proporciona instrucciones paso a paso que muestran cómo crear y probar un modelo que muestra los contactos en una lista externa de SharePoint.|
|[Integración de datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Proporciona información general sobre la creación y el diseño de modelos para el servicio BDC.|
