---
title: "Dise&#241;ar un modelo de conectividad a datos profesionales | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], diseñar un modelo"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], diseñar un modelo"
ms.assetid: 19cad8cf-8a82-4000-84cf-1e5aff54e5af
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Dise&#241;ar un modelo de conectividad a datos profesionales
  Puede desarrollar un modelo para el servicio Conectividad a datos profesionales agregando entidades y métodos a un archivo del modelo.  Una entidad describe una colección de campos de datos.  Por ejemplo, una entidad puede representar una tabla en una base de datos.  Un método realiza una tarea, por ejemplo, agrega, elimina o actualiza los datos representados por las entidades.  Para obtener más información, vea [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## Agregar entidades  
 Puede agregar una entidad arrastrando o copiando **Entidad** de Visual Studio **Cuadro de herramientas** al diseñador de BDC.  Para obtener más información, vea [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Defina los campos de la entidad en una clase.  Por ejemplo, puede agregar un campo denominado `Address` a una clase `Customer`.  Puede agregar una nueva clase al proyecto o usar una clase existente creada a través de otras herramientas, como Object Relational Designer.  El nombre de la entidad y el nombre de la clase que representa la entidad no tienen que coincidir.  Cuando defina los métodos del modelo, relacione la clase con la entidad.  
  
## Agregar métodos  
 El Servicio de BDC llama a los métodos del modelo cuando los usuarios ven, agregan, actualizan o eliminan información de una lista o elemento web basados en el modelo.  Debe agregar al modelo un método para cada una de las tareas que el usuario puede realizar.  Para crear métodos, seleccione cualquiera de los cinco tipos de métodos básicos de la ventana **Detalles del método de BDC**.  En la tabla siguiente se describen los cinco métodos básicos de un modelo BDC.  
  
|Método|Descripción|  
|------------|-----------------|  
|Finder|Devuelve una colección de instancias de entidad.  Se invoca cuando el usuario abre una lista o elemento web.  Para obtener más información, vea [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md).|  
|Specific Finder|Devuelve una instancia de entidad concreta.  Se invoca cuando un usuario ve los detalles de un elemento concreto de una lista.  Para obtener más información, vea [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Creator|Agrega nuevos datos al origen de datos de una entidad.  Se invoca cuando los usuarios elija el botón de **Nuevo elemento** en la cinta de opciones de una lista basada en el modelo.  Para obtener más información, vea [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md).|  
|Updater|Modifica los datos de una lista.  Se invoca cuando los usuarios actualizan la información de una lista.  Para obtener más información, vea [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md).|  
|Deleter|Quita datos.  Se invoca cuando los usuarios eliminan un elemento de la lista.  Para obtener más información, vea [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## Definir los parámetros de los métodos  
 Cuando se crea un método, Visual Studio agrega los parámetros de entrada y salida que son adecuados para ese tipo de método.  Estos parámetros son solo marcadores de posición.  En la mayoría de los casos, es necesario modificar los parámetros para que pasen o devuelvan el tipo correcto de datos.  Por ejemplo, de forma predeterminada, un método Finder devuelve una cadena.  En la mayoría de los casos, le interesará modificar el parámetro de devolución del método Finder para que devuelva una colección de entidades.  Para ello, puede modificar el descriptor de tipo del parámetro.  Un descriptor de tipo es una colección de atributos que describe el tipo de datos de un parámetro.  Para obtener más información, vea [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Visual Studio permite copiar descriptores de tipo entre los parámetros del modelo.  Por ejemplo, puede definir un descriptor de tipo denominado `CustomerTD` para el parámetro de devolución del método `GetCustomer`.  Puede copiar el descriptor de tipo `CustomerTD` en el **Explorador de BDC** y pegarlo a continuación en el parámetro de entrada del método `CreateCustomer`.  De este modo, no tendrá que definir el mismo descriptor de tipo varias veces.  
  
##  <a name="MethodInstances"></a> Instancias de métodos  
 Cuando crea un método, Visual Studio agrega una instancia predeterminada del método.  Una instancia de método es una referencia a un método junto con los valores predeterminado de los parámetros.  Un único método puede tener varias instancias de método.  Cada instancia es una combinación de la firma del método y un conjunto de valores predeterminados.  Para obtener más información, vea [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Cuando se ejecuta el proyecto, las instancias de método aparecen en una lista desplegable sobre la lista de SharePoint.  Los usuarios pueden elegir las instancias de método para ver los datos.  
  
 Para agregar valores predeterminados a la instancia de método, es necesario modificar directamente el código XML del modelo.  Para obtener más información, vea [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## Agregar descriptores de filtro  
 Es posible que los consumidores del modelo deseen recuperar las instancias de una entidad que coincida con ciertos criterios.  Para habilitar esta funcionalidad, puede agregar un descriptor de filtro a un método.  Los descriptores de filtro permiten a los consumidores del modelo filtrar los conjuntos de resultados de un método pasando los valores a los métodos antes de ejecutarlos.  Para obtener más información, vea [Cómo: Agregue los parámetros de filtro a las operaciones a las instancias del límite del sistema externo](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint cuenta con diversas características que permiten a los usuarios proporcionar valores de filtro.  Por ejemplo, los elementos web de datos profesionales proporcionan un cuadro de texto de filtro.  Los usuarios pueden limitar los datos de una lista especificando un valor en el cuadro de texto.  Para obtener más información acerca de cómo se agrega un descriptor de filtro a un método, vea [Cómo: Agregar un descriptor de filtro para un método Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### Propiedades del descriptor de filtro  
 Es necesario establecer el valor de las propiedades **Associated Type Descriptor**, **Name** y **Type** de un descriptor de filtro.  Todas las demás propiedades son opcionales.  
  
 La propiedad **Associated Type Descriptor** relaciona el descriptor de filtro con un parámetro de entrada.  Cuando un usuario proporciona un valor de filtro, el Servicio de BDC pasa ese valor al método a través del parámetro de entrada.  
  
 La propiedad **Type** describe el modelo de filtrado que se desea usar.  En SharePoint, el modelo de filtrado seleccionado afecta al texto que aparece en la interfaz de usuario.  Por ejemplo, en un modelo de filtrado de comparación, el texto **es igual a** aparece como un control sobre un elemento web de datos profesionales.  Para obtener más información sobre cada modelo de filtrado, vea [Tipos de filtros que admite el BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Para obtener más información sobre las propiedades de un descriptor de filtro, [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280)vea.  
  
### Proporcionar valores predeterminados  
 En ciertos casos, puede ocurrir que el usuario no proporcione ningún valor de filtro.  Para proporcionar un valor predeterminado, puede agregarse un valor predeterminado a la instancia de método o puede establecerse el valor predeterminado en el código del método.  Para obtener más información sobre cómo agregar un valor predeterminado a la instancia de método, vea [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  Para obtener un ejemplo acerca de cómo se establece el valor predeterminado de un parámetro de entrada en el código del método, vea [Cómo: Agregar un descriptor de filtro para un método Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## Validar el modelo  
 Puede validar el modelo durante la fase de desarrollo.  Visual Studio identifica los problemas que pueden impedir que el modelo se comporte del modo esperado.  Estos problemas se muestran en la **Lista de errores** de Visual Studio.  
  
 Puede validar un modelo abriendo el menú contextual para el diseñador de BDC y elige **validar**.  Si el modelo contiene algún error, aparecen en **Lista de errores**.  Puede mover rápidamente al código que contiene un error haciendo doble clic en el error en la lista.  Como alternativa, puede elegir F8 o claves mayús\+f8 repetidamente para avanzar o retroceder con errores de la lista.  
  
 Los errores de validación pueden producirse cuando se infringen de algún modo las reglas del modelo.  Por ejemplo, si la propiedad **IsCollection** de un descriptor de tipo está establecida en **true** pero no existen descriptores de tipo secundarios, se producirá un error de validación.  Es posible que tenga que consultar las reglas de un modelo BDC para entender algunos errores que aparecen en la **Lista de errores** de Visual Studio.  Para obtener más información sobre las reglas de un modelo BDC, vea. [Esquema de BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275)  
  
## Depurar la solución que contiene el modelo  
 Puede depurar su código del mismo modo que depuraría cualquier código de Visual Studio.  Para depurar el código, establezca los puntos de interrupción en cualquier parte del código e inicie el depurador.  Visual Studio abre el sitio de SharePoint.  En SharePoint, cree una lista o elemento web que use sus datos profesionales.  A continuación, podrá recorrer el código.  Para obtener más información sobre la depuración de proyectos de SharePoint, vea [Solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 También puede depurar el código de los ensamblados personalizados que agrega al proyecto.  Sin embargo, para depurar el código de un ensamblado personalizado, debe agregar el ensamblado al paquete de la solución.  Para obtener más información, vea [Cómo: Agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Para obtener más información acerca de cómo se agrega un ensamblado personalizado al proyecto, vea [Cómo: Incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### Configurar la seguridad de BDC  
 Quizás necesite modificar la configuración de seguridad de SharePoint para poder depurar la solución.  Para modificar estos valores, abra la aplicación de Servicio de conectividad a datos profesionales en el sitio web Administración central de SharePoint 2010.  En el cuadro de diálogo **Establecer permisos del Repositorio de metadatos**, especifique su cuenta de usuario y, a continuación, seleccione alguna de las siguientes opciones:  
  
|Tarea|Opción|  
|-----------|------------|  
|Para implementar modelos en el Servicio de BDC.|Editar|  
|Para crear listas y elementos web usando tipos de contenido externo \(entidades\) del modelo.|Seleccionable en clientes|  
|Para crear, leer, actualizar y eliminar datos de entidades.|Ejecutar|  
  
 Para obtener más información sobre estos valores, vea [Administración del servicio conectividad a datos profesionales](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 También puede establecer los permisos de seguridad para modelos o tipos de contenido externo concretos.  Para obtener más información sobre cómo establecer permisos de seguridad de un modelo, vea [Administración del modelo BDC](http://go.microsoft.com/fwlink/?LinkID=178884).  Para obtener más información sobre cómo establecer permisos de seguridad de un tipo de contenido externo, vea [Administración externa de tipo de contenido](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Use estos valores para depurar una solución en el servidor local de SharePoint.  Para obtener más información sobre cómo configurar la configuración de seguridad BDC\- relacionadas en el servidor de producción de SharePoint, vea [Información general de seguridad de Servicios de conectividad a datos profesionales](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### Retirar modelos dañados  
 La primera vez que se inicia el depurador, Visual Studio implementa el modelo completo en SharePoint.  A partir de ese momento, Visual Studio actualiza el modelo de SharePoint con los cambios realizados entre las distintas implementaciones.  
  
 Puede haber casos en los que desee que Visual Studio retire completamente el modelo de SharePoint.  Por ejemplo, si un modelo se ha dañado.  Para implementar de nuevo el modelo en SharePoint, establezca la propiedad **Incremental Update** del modelo en **False** y, a continuación, inicie el depurador.  La propiedad **Incremental Update** aparece en la ventana **Propiedades** cuando se selecciona el nodo que representa el modelo en el **Explorador de BDC**.  De forma predeterminada, el nombre del modelo es **BdcModel1**.  
  
### Cambiar los nombres de identificador de las entidades del modelo  
 Si cambia el nombre de un identificador después de implementar el modelo, podría producirse un error de implementación.  Este error no puede resolverse estableciendo la propiedad **Incremental Update** del modelo en **False**.  Debe retirar el modelo manualmente y, a continuación, implementar de nuevo la solución.  Para obtener más información, vea [Solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  Para evitar este error, puede establecer la propiedad **Incremental Update** en **False** antes de implementar por primera vez el modelo.  
  
## Buscar documentación sobre los elementos del modelo BDC  
 Visual Studio agrega al modelo un elemento XML para cada entidad, método u otro elemento que se cree.  Los atributos del elemento aparecen como propiedades en la ventana **Propiedades**.  Para obtener información sobre los elementos y atributos que Visual Studio genera cuando se diseña el modelo, vea [Esquema de BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)|Describe las herramientas que pueden usarse para diseñar un modelo de BDC visualmente.|  
|[Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)|Muestra cómo se agregan tipos de contenido externo o entidades al modelo.|  
|[Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)|Muestra cómo se agrega un método que permite a los usuarios ver una lista de entidades en una lista o elemento web.|  
|[Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)|Muestra cómo se agrega un método que permite a los usuarios ver los detalles de una entidad concreta.|  
|[Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)|Muestra cómo se agrega un método que permite a los usuarios agregar registros directamente a un origen de datos desde una lista o elemento web.|  
|[Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)|Muestra como se agrega un método que permite a los usuarios quitar datos de un origen de datos usando las opciones de la interfaz de usuario de una lista o elemento web.|  
|[Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)|Muestra cómo se agrega un método que permite a los usuarios cambiar registros de datos de un origen de datos directamente desde una lista o elemento web.|  
|[Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Muestra cómo se usa la ventana Detalles del método de Visual Studio para agregar los parámetros de entrada y devolución a un método.|  
|[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Muestra cómo se definen tipos de datos de parámetros en el modelo.|  
|[Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)|Muestra cómo se crea una instancia de un método que BDC ejecuta.|  
|[Cómo: Agregar un descriptor de filtro para un método Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Muestra cómo se permite que los usuarios limiten el número de instancias devueltas por un método Finder.|  
|[Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)|Describe cómo se pueden definir relaciones entre las entidades del modelo.  Los elementos web de datos profesionales, las listas externas y las aplicaciones personalizadas pueden mostrar estas relaciones de datos en una interfaz de usuario.|  
|[Cómo crear una asociación entre entidades](../sharepoint/how-to-create-an-association-between-entities.md)|Muestra cómo se definen relaciones entre las entidades del modelo.|  
|[Tutorial: Crear una lista externa en SharePoint con datos profesionales](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Proporciona instrucciones paso a paso acerca de cómo se crea y se prueba un modelo que muestra los contactos de una lista externa de SharePoint.|  
|[Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Proporciona información general sobre la creación y el diseño de modelos del Servicio de BDC.|  
  
  