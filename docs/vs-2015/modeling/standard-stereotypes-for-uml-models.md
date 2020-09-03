---
title: Estereotipos estándar para modelos UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a16c68b3b14be57fb0a6a45c740e5420a82c2ddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661048"
---
# <a name="standard-stereotypes-for-uml-models"></a>Estereotipos estándar para modelos UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede agregar estereotipos a los elementos del modelo UML para proporcionar información adicional para el lector o para el procesamiento de la máquina. Los estereotipos se definen en perfiles y cada perfil proporciona un conjunto de estereotipos. Algunos perfiles se proporcionan con Visual Studio. También puede definir sus propios perfiles que pueden contener sus propios estereotipos. Para obtener más información, vea [definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="the-standard-profiles"></a>Los perfiles estándar
 Los siguientes perfiles estarán disponibles en una edición compatible de Visual Studio en cuanto la haya instalado.

|Perfil|Propósito|
|-------------|-------------|
|[Perfil estándar UML L2](#L2)|Un conjunto estándar de estereotipos que se pueden usar para agregar información adicional sobre un elemento o una relación.|
|[Perfil estándar UML L3](#L3)|Un conjunto estándar de estereotipos que se pueden usar para agregar información adicional sobre un elemento o una relación.|
|[Perfil de C#](#NetProfile)|Si desea que una clase u otro elemento en un modelo UML represente código de programa, puede indicarlo aplicando uno de los estereotipos del perfil de C#.<br /><br /> Estos estereotipos también agregan propiedades a los elementos del modelo.|

 Cuando se crea un nuevo modelo UML, los perfiles estándar UML L2 y L3 se vinculan al modelo, a menos que quite los vínculos.

 Para usar los estereotipos en cualquiera de estos perfiles, primero debe vincular el perfil a un paquete o un modelo que contenga los elementos a los que desea aplicarlos.

#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Para vincular un perfil a un modelo o un paquete

1. Abra el **Explorador de modelos UML**. En el menú **arquitectura** , elija **ventanas**y, a continuación, haga clic en **Explorador de modelos UML**.

2. Busque un paquete o un modelo que contenga todos los elementos a los que desea aplicar los estereotipos del perfil.

3. Haga clic con el botón secundario en el paquete o el modelo y, a continuación, haga clic en **propiedades**.

4. En la ventana **propiedades** , establezca la propiedad **perfiles** en los perfiles que desee.

#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>Para quitar el vínculo entre un perfil y un modelo o paquete

1. En el explorador de modelos UML, haga clic con el botón secundario en el modelo o paquete y, a continuación, haga clic en **propiedades**.

2. En el ventana Propiedades, establezca la propiedad **profiles** en Empty.

    > [!NOTE]
    > Puede desvincular un perfil solo si ninguno de los elementos en el modelo o el paquete usan los estereotipos de ese perfil.

#### <a name="to-apply-a-stereotype-to-a-model-element"></a>Para aplicar un estereotipo a un elemento del modelo

1. Haga clic con el botón secundario en el elemento de modelo en un diagrama o en el **Explorador de modelos UML**y, a continuación, haga clic en **propiedades**.

2. Haga clic en la propiedad **estereotipos** y seleccione los estereotipos que desea aplicar.

     Los estereotipos seleccionados aparecen entre «comillas angulares» en el elemento del modelo, para casi todos los tipos de elemento.

    > [!NOTE]
    > Si no puede ver la propiedad **estereotipos** , o si el estereotipo que desea no aparece, compruebe que el elemento de modelo está dentro de un paquete o un modelo al que se ha vinculado el perfil adecuado.

3. Algunos estereotipos permiten establecer los valores de las propiedades adicionales para el elemento del modelo. Para ver estas propiedades, expanda la propiedad **estereotipos** .

### <a name="uml-standard-profile-l2"></a><a name="L2"></a> Perfil estándar UML L2
 Los estereotipos siguientes se pueden usar para especializar el significado de los elementos del modelo UML, a menos que el vínculo al perfil se haya quitado del modelo.

 El significado exacto de estos estereotipos está determinado por las convenciones locales y por las herramientas que puede usar para procesar el modelo.

|Estereotipo|Se aplica a|Significado|
|----------------|----------------|-------------|
|auxiliary|Clase|Una clase que es compatible con otra clase, normalmente mediante la implementación de lógica adicional. La otra clase puede tener el estereotipo «focus».|
|llamada|Dependencia|La clase de cliente llama a las operaciones del proveedor.|
|create|Dependencia|La clase de cliente llama a las instancias del proveedor.|
|create|Message|El remitente crea el receptor.|
|create|Operación|Esta operación es un constructor.|
|derive|Dependencia|El elemento de cliente se calcula total o parcialmente desde el proveedor.|
|destroy|Operación|La operación destruye su instancia.|
|documento|Artefacto|Un «archivo» que no es un origen o un archivo ejecutable.|
|Entidad|Componente|El componente representa un concepto del negocio.|
|ejecutable|Artefacto|Un «archivo» ejecutable.|
|archivo|Artefacto|Un archivo físico|
|foco|Clase|Una clase que define la lógica de negocios principal, que es compatible con varias clases «auxiliares».|
|marco de trabajo|Paquete|Este paquete define un modelo de diseño reutilizable.|
|implement|Componente|La implementación de una «especificación».|
|implementationClass|Clase|La clase describe una implementación y cada instancia en tiempo de ejecución tiene una clase de implementación fija. Contraste con «tipo».|
|instantiate|Dependencia|El cliente crea instancias del proveedor.|
|biblioteca|Artefacto|Un «archivo» de biblioteca.|
|metaclass|Clase|Las instancias de esta clase también son clases.|
|modelLibrary|Paquete|Contiene elementos del modelo diseñados para reutilizarse en paquetes de importación. Normalmente se define como parte de un perfil y se importa automáticamente mediante la aplicación del perfil.|
|proceso|Componente|Un componente basado en transacciones o que transporta un subproceso.|
|realization|Clase, interfaz, componente|Describe una implementación.|
|refine|Dependencia|La clase de cliente, componente o paquete proporciona más información sobre la especificación o diseño que el proveedor.|
|responsibility|Dependencia|El comentario en el extremo del proveedor de la dependencia define las responsabilidades de la clase de cliente o el componente.|
|script|Artefacto|Un «archivo» interpretable.|
|Enviar|Dependencia|La operación de origen envía la señal de destino.|
|service|Componente|Un componente sin estado.|
|source|Artefacto|Un «archivo» compilable.|
|specification|Clase, interfaz, componente|Define el comportamiento de un componente u objeto sin definir cómo funciona internamente.|
|subsistema|Componente|Una parte de un sistema grande. Un subsistema de un diagrama de casos de uso es un componente con el estereotipo del subsistema.|
|seguimiento|Dependencia|El elemento de cliente forma parte del diseño que desarrolla el proveedor. Los dos extremos de esta dependencia normalmente están en modelos diferentes. Uno de estos modelos es una realización del otro.|
|type|Clase|Especifica el comportamiento de un objeto sin indicar cómo se implementa. Un objeto es un miembro de un tipo si se ajusta a la especificación.|
|utilidad|Clase|Una colección de funciones estáticas. La clase no tiene instancias.|

### <a name="uml-standard-profile-l3"></a><a name="L3"></a> Perfil estándar UML L3
 Los estereotipos siguientes se pueden usar para especializar el significado de los elementos del modelo UML, a menos que el perfil se haya desvinculado del modelo.

 El significado exacto de estos estereotipos está determinado por las convenciones locales y por las herramientas que puede usar para procesar el modelo.

|Estereotipo|Se aplica a|Descripción|
|----------------|----------------|-----------------|
|buildComponent|Componente|Una colección de elementos utilizados para definir una compilación.|
|metaModel|Modelo|Define un lenguaje de modelos como una variante de UML o un lenguaje específico de dominio.|
|systemModel|Modelo|Un modelo que es una colección de modelos que se aplican al mismo sistema, por ejemplo, una especificación, una realización y relaciones de seguimiento entre ellos.|

## <a name="c-profile"></a><a name="NetProfile"></a> Perfil de C#
 Los estereotipos definidos en este perfil permiten indicar que un elemento del modelo está pensado para traducción en el código del programa. Cada estereotipo define propiedades adicionales que se pueden establecer en el elemento del modelo.

 Para que estos estereotipos estén disponibles, vincule un modelo o paquete al perfil de C#. A continuación, puede aplicar los estereotipos a elementos del modelo en ese modelo o paquete.

 En la siguiente tabla se resumen los estereotipos disponibles, los elementos a los que se aplican y las propiedades adicionales que están disponibles.

|Estereotipo|Se aplica a|Propiedades|
|----------------|----------------|----------------|
|**Clase de C#**|Clase UML<br /><br /> Componente|**Atributos CLR**<br /><br /> **Is Partial**<br /><br /> **Está sellado**<br /><br /> **Is Static**<br /><br /> **Is Unsafe**<br /><br /> **Visibilidad de los paquetes**|
|**Struct de C#**|Clase UML<br /><br /> Componente|**Atributos CLR**<br /><br /> **Is Partial**<br /><br /> **Is Unsafe**<br /><br /> **Visibilidad de los paquetes**|
|**Miembros globales de C#**|Clase UML<br /><br /> Componente|**Atributos CLR**|
|**Interfaz de C#**|Interfaz de C#|**Atributos CLR**<br /><br /> **Is Partial**<br /><br /> **Visibilidad de los paquetes**|
|**C# enum**|Enumeración UML|**Atributos de Clr**<br /><br /> **Tipo base**|
|**Espacio de nombres de C#**|Paquete UML|**Atributos CLR**<br /><br /> **Nombre base**<br /><br /> **Uso de espacios de nombres**|

## <a name="see-also"></a>Consulte también
 [Agregar estereotipos a elementos del modelo UML](../modeling/add-stereotypes-to-uml-model-elements.md) [personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md)
