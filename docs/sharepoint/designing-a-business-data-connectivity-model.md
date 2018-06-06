---
title: Diseñar un modelo de conectividad a datos empresariales | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d0971dc9d445c7a492d934c0c2bdc9b47de92028
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766069"
---
# <a name="design-a-business-data-connectivity-model"></a>Diseñar un modelo de conectividad a datos empresariales
  Puede desarrollar un modelo para el servicio de conectividad de datos profesionales (BDC) agregando entidades y métodos a un archivo de modelo. Una entidad describe una colección de campos de datos. Por ejemplo, una entidad puede representar una tabla en una base de datos. Un método realiza una tarea, como agregar, eliminar o actualizar datos representados por las entidades. Para obtener más información, consulte [integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="add-entities"></a>Agregar entidades
 Puede agregar una entidad arrastrando o copiando una **entidad** desde Visual Studio **cuadro de herramientas** en el Diseñador de BDC. Para obtener más información, consulte [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Define los campos de la entidad en una clase. Por ejemplo, puede agregar un campo denominado `Address` a una `Customer` clase. Puede agregar una nueva clase al proyecto o utilizar una clase existente que se crea mediante otras herramientas como el Object Relational Designer (Object Relational Designer). El nombre de la entidad y el nombre de la clase que representa la entidad no tienen que coincidir. Relacione la clase a la entidad al definir los métodos en el modelo.  
  
## <a name="add-methods"></a>Agregar métodos
 El servicio BDC llama a métodos en el modelo cuando los usuarios ver, agregarán, actualización o eliminen la información en una lista o un elemento Web que se basa en el modelo. Debe agregar un método al modelo para cada tarea que el usuario puede realizar. Crear métodos haciendo clic en cualquiera de los cinco tipos de método básico de la **detalles del método de BDC** ventana. La tabla siguiente describen los cinco métodos básicos de un modelo BDC.  
  
|Método|Descripción|  
|------------|-----------------|  
|Método Finder|Devuelve una colección de instancias de entidad. Se llama cuando el usuario abra la lista o el elemento Web. Para obtener más información, consulte [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md).|  
|método Finder específico|Devuelve una instancia de entidad concreta. Se llama cuando un usuario ve los detalles de un elemento específico en una lista. Para obtener más información, consulte [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Creator|Agrega nuevos datos al origen de datos de una entidad. Se llama cuando los usuarios elegir la **nuevo elemento** botón en la cinta de opciones de una lista que se basa en el modelo. Para obtener más información, consulte [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md).|  
|Updater|Modifica los datos en una lista. Se llama cuando los usuarios actualizar información en una lista. Para obtener más información, consulte [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md).|  
|Deleter|Quita los datos. Se llama cuando los usuarios eliminan un elemento de la lista. Para obtener más información, consulte [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## <a name="define-method-parameters"></a>Definir parámetros de método
 Cuando se crea un método, Visual Studio agrega los parámetros de entrada y salidos que son adecuados para el tipo de método. Estos parámetros son solo marcadores de posición. En la mayoría de los casos, debe modificar los parámetros para que puedan pasan o devuelven el tipo de datos correcto. Por ejemplo, de forma predeterminada, un método Finder devuelve una cadena. En la mayoría de los casos que desea modificar el parámetro devuelto del método Finder para que devuelva una colección de entidades. Puede hacerlo modificando el descriptor de tipo del parámetro. Un descriptor de tipo es una colección de atributos que describe el tipo de datos de un parámetro. Para obtener más información, consulte [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Visual Studio permite copiar descriptores de tipo entre los parámetros en el modelo. Por ejemplo, podría definir un descriptor de tipos denominado `CustomerTD` para el parámetro de valor devuelto de la `GetCustomer` método. Puede copiar la `CustomerTD` escriba descriptor en la **Explorador de BDC**y, a continuación, pegue ese descriptor de tipo para el parámetro de entrada de la `CreateCustomer` método. Esto evita tener que definir el mismo descriptor de tipo de más de una vez.  
  
## <a name="method-instances"></a>Instancias (método)
 Cuando se crea un método, Visual Studio agrega una instancia predeterminada del método. Una instancia de método es una referencia a un método, junto con los valores predeterminados para los parámetros. Un único método puede tener varias instancias de método. Cada instancia es una combinación de la firma del método y un conjunto de valores predeterminados. Para obtener más información, consulte [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Al ejecutar el proyecto, instancias de método aparecen en una lista desplegable situada encima de la lista de SharePoint. Los usuarios pueden elegir las instancias de método para ver los datos.  
  
 Para agregar valores predeterminados a la instancia de método, tendrá que modificar directamente el XML del modelo. Para obtener más información, consulte [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## <a name="add-filter-descriptors"></a>Agregar descriptores de filtro
 Los consumidores del modelo que desee recuperar instancias de una entidad que cumplen algunos criterios. Para habilitar esta funcionalidad, puede agregar un descriptor de filtro a un método. Descriptores de filtro permiten a los consumidores del modelo filtrar los conjuntos de resultados del método pasando valores a los métodos antes de ejecutarlos. Para obtener más información, consulte [Cómo: agregar parámetros de filtro a las operaciones en instancias de límite desde el sistema externo](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint proporciona varias características que permiten a los usuarios proporcionar valores de filtro. Por ejemplo, elementos Web de datos profesionales proporcionan un cuadro de texto de filtro. Los usuarios pueden limitar los datos en una lista escribiendo un valor en el cuadro de texto. Para obtener más información sobre cómo agregar un descriptor de filtro a un método, consulte [Cómo: agregar un Descriptor de filtro a un método de buscador](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### <a name="filter-descriptor-properties"></a>Propiedades de descriptor de filtro
 Debe establecer el valor de la **Associated Type Descriptor**, **nombre**, y **tipo** propiedades de un descriptor de filtro. Todas las demás propiedades son opcionales.  
  
 El **Associated Type Descriptor** propiedad se relaciona con el descriptor de filtro a un parámetro de entrada. Cuando un usuario proporciona un valor de filtro, el servicio BDC pasa ese valor en el método mediante el parámetro de entrada.  
  
 El **tipo** propiedad describe el modelo de filtrado que se va a utilizar. En SharePoint, el modelo de filtrado seleccionado afecta al texto que aparece en la interfaz de usuario (IU). Por ejemplo, para un modelo de filtrado de comparación, el texto **es igual a** aparece como un control por encima de un elemento Web de datos de empresa. Para obtener más información acerca de cada modelo de filtrado, consulte [tipos de filtros admitidos por la BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Para obtener más información acerca de las propiedades de un descriptor de filtro, vea [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### <a name="provide-default-values"></a>Proporcionar los valores predeterminados
 En algunos casos, el usuario no puede proporcionar un valor de filtro. Puede proporcionar un valor predeterminado mediante la adición de un valor predeterminado para la instancia de método, o estableciendo el valor predeterminado en el código del método. Para obtener más información acerca de cómo agregar un valor predeterminado a la instancia de método, consulte [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Para obtener un ejemplo de cómo establecer el valor predeterminado de un parámetro de entrada en el código del método, consulte [Cómo: agregar un Descriptor de filtro a un método de buscador](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## <a name="validate-the-model"></a>Validar el modelo
 Puede validar el modelo durante el desarrollo. Visual Studio identifica los problemas que pueden impedir que el modelo se comporta según lo esperado. Estos problemas se muestran en Visual Studio **lista de errores**.  
  
 Puede validar un modelo, abriendo el menú contextual para el Diseñador de BDC y, a continuación, elija **validar**. Si el modelo contiene los errores, que aparecen en la **lista de errores**. Puede mover rápidamente el cursor en el código que contiene un error haciendo doble clic en el error en la lista. Como alternativa, puede elegir la **F8** o **MAYÚS**+**F8** claves repetidamente al paso hacia delante o hacia atrás a través de los errores en la lista.  
  
 Cuando se infringen las reglas del modelo de alguna manera, pueden producirse errores de validación. Por ejemplo, si la **IsCollection** propiedad de un descriptor de tipo está establecida en **true**, pero no descriptores de tipo secundario existen, aparecerá un error de validación. Es posible que deba hacer referencia a las reglas de un modelo BDC para entender algunos errores que aparecen en Visual Studio **lista de errores**. Para obtener más información acerca de las reglas de un modelo BDC, vea [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="debug-the-solution-that-contains-the-model"></a>Depurar la solución que contiene el modelo
 Puede depurar el código como se haría con cualquier código en Visual Studio. Para depurar el código, establezca puntos de interrupción en cualquier lugar en el código y, a continuación, iniciar al depurador. Visual Studio abre el sitio de SharePoint. En SharePoint, cree una lista o un elemento Web que utiliza datos de su empresa. A continuación, puede recorrer el código. Para obtener más información sobre la depuración de proyectos de SharePoint, vea [solución de problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 También puede depurar código en ensamblados personalizados que agregue al proyecto. Sin embargo, para depurar código en un ensamblado personalizado, debe agregar el ensamblado al paquete de solución. Para obtener más información, consulte [Cómo: agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Para obtener más información acerca de cómo agregar un ensamblado personalizado al proyecto, vea [Cómo: incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### <a name="configure-bdc-security"></a>Configurar la seguridad BDC
 Es posible que deba modificar la configuración de seguridad de SharePoint antes de poder depurar la solución. Para modificar esta configuración, abra la aplicación de servicio de conectividad de datos empresariales en el sitio Web de SharePoint 2010 Central Administration. En el **establecer permisos del almacén de metadatos** cuadro de diálogo, agregue la cuenta de usuario y, a continuación, seleccione cualquiera de las siguientes opciones:  
  
|Tarea|Opción|  
|----------|------------|  
|Para implementar modelos en el servicio BDC.|Editar|  
|Para crear listas y los elementos Web mediante el uso externo tipos de contenido (entidades) en el modelo.|Seleccionable en clientes|  
|Para crear, leer, actualizar y eliminar datos de la entidad.|Ejecutar|  
  
 Para obtener más información acerca de estas opciones, consulte [administración del servicio de conectividad a datos empresariales](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 También puede establecer permisos de seguridad para los modelos individuales o tipos de contenido externo. Para obtener más información sobre cómo establecer los permisos de seguridad de un modelo, vea [administración del modelo BDC](http://go.microsoft.com/fwlink/?LinkID=178884). Para obtener más información sobre cómo establecer los permisos de seguridad de un tipo de contenido externo, vea [administración del tipo de contenido externo](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Use estas opciones para depurar una solución en el servidor de SharePoint local. Para obtener más información acerca de cómo configurar opciones de seguridad relativos a BDC en servidor de SharePoint de producción, consulte [Introducción a la seguridad Business Data Connectivity Services](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### <a name="retract-models-that-become-corrupt"></a>Retirar modelos dañados
 La primera vez que inicie al depurador, Visual Studio implementa el modelo completo en SharePoint. Para cada hora a partir de ahí, Visual Studio actualiza el modelo de SharePoint con los cambios realizados entre las distintas implementaciones.  
  
 Puede haber situaciones donde desea que Visual Studio Retire completamente el modelo de SharePoint. Por ejemplo, un modelo podría dañarse.  Para volver a implementar el modelo en SharePoint, establezca la **actualización Incremental** propiedad del modelo para **False**, y, a continuación, iniciar el depurador. El **actualización Incremental** propiedad aparece en la **propiedades** ventana cuando se selecciona el nodo que representa el modelo en el **Explorador de BDC**. De forma predeterminada, el nombre del modelo es **BdcModel1**.  
  
### <a name="change-identifier-names-of-entities-in-the-model"></a>Cambiar nombres de identificador de las entidades del modelo
 Si cambia el nombre de un identificador después de implementar el modelo, puede aparecer un error de implementación. No se puede resolver este error estableciendo la **actualización Incremental** propiedad del modelo para **False**. Debe retirar el modelo manualmente y, a continuación, vuelva a implementar la solución. Para obtener más información, consulte [solución de problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). Puede evitar este error estableciendo la **actualización Incremental** propiedad **False** antes de implementar inicialmente el modelo.  
  
## <a name="locate-documentation-for-bdc-model-elements"></a>Buscar documentación de elementos del modelo BDC
 Visual Studio agrega un elemento XML en el modelo para cada entidad, método u otro elemento que cree. Atributos del elemento aparecen como propiedades en el **propiedades** ventana. Para obtener información acerca de los elementos y atributos que genera Visual Studio cuando se diseña el modelo, vea [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="related-topics"></a>Temas relacionados
  
|Título|Descripción|  
|-----------|-----------------|  
|[Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)|Describe las herramientas que puede usar para diseñar visualmente un modelo de BDC.|  
|[Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)|Muestra cómo agregar tipos de contenido externo o entidades, en el modelo.|  
|[Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)|Muestra cómo agregar un método que permite a los usuarios ver una lista de entidades en una lista o un elemento Web.|  
|[Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)|Muestra cómo agregar un método que permite a los usuarios ver los detalles de una entidad específica.|  
|[Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)|Muestra cómo agregar un método que permite a los usuarios agregar registros a un origen de datos directamente desde una lista o un elemento Web.|  
|[Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)|Muestra cómo agregar un método que permite a los usuarios quitar datos de un origen de datos mediante opciones de la interfaz de usuario (IU) de una lista o elemento Web.|  
|[Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)|Muestra cómo agregar un método que permite a los usuarios cambiar registros de datos de un origen de datos directamente desde una lista o un elemento Web.|  
|[Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Muestra cómo utilizar la ventana de detalles de método en Visual Studio para agregar parámetros de entrada y salidos a un método.|  
|[Cómo: Definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Muestra cómo definir tipos de datos de parámetro en el modelo.|  
|[Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)|Muestra cómo crear una instancia de un método que se ejecuta la BDC.|  
|[Cómo: Agregar un descriptor de filtro para un método Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Muestra cómo permitir a los usuarios limitar el número de instancias devueltas por un método Finder.|  
|[Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)|Describe cómo puede definir las relaciones entre las entidades del modelo. Elementos Web de datos profesionales, listas externas y las aplicaciones personalizadas pueden mostrar estas relaciones de datos en una interfaz de usuario (UI).|  
|[Cómo: crear una asociación entre entidades](../sharepoint/how-to-create-an-association-between-entities.md)|Muestra cómo definir las relaciones entre las entidades del modelo.|  
|[Tutorial: Crear una lista externa en SharePoint mediante empresariales](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Proporciona instrucciones paso a paso que muestran cómo crear y probar un modelo que muestra los contactos en una lista externa de SharePoint.|  
|[Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Proporciona información general de crear y diseñar modelos para el servicio BDC.|  
  
