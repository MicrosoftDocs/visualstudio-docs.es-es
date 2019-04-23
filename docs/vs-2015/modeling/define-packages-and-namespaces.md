---
title: Definir paquetes y espacios de nombres | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cb0502128b95716b0598b373be81519a06911f06
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052810"
---
# <a name="define-packages-and-namespaces"></a>Definir espacios de nombres y paquetes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, un *paquete* es un contenedor para las definiciones de elementos UML, como clases, casos de uso y los componentes. Un paquete también puede contener otros paquetes.  
  
 En el Explorador de modelos UML, todas las definiciones dentro de un paquete se anidan bajo el paquete. El modelo UML es un tipo de paquete y forma la raíz del árbol.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>En este tema  
 [Espacios de nombres](#Namespaces)  
  
 [Crear y ver paquetes](#Packages)  
  
 [Crear elementos del modelo dentro de paquetes](#Elements)  
  
 [Mover elementos dentro o fuera de un paquete](#Moving)  
  
 [Pegar elementos en un paquete](#Pasting)  
  
 [Importar relaciones entre paquetes](#Import)  
  
 [Referencias a uno Namespace a otro](#References)  
  
 [Propiedades de paquetes](#Properties)  
  
## <a name="Namespaces"></a> espacios de nombres  
 Los paquetes son útiles para estructurar el trabajo en diferentes áreas. Cada paquete define un espacio de nombres para que los nombres definidos en paquetes diferentes no entren en conflicto entre sí.  
  
 La propiedad de nombre completo de cada elemento es el nombre completo del paquete al que pertenece, seguido del propio nombre del elemento. Por ejemplo, si el paquete se denomina `MyPackage`, una clase dentro del paquete tendrá un nombre completo como `MyPackage::MyClass`. Dado que cada elemento se incluye dentro de un modelo, cada nombre completo comienza con el nombre del modelo.  
  
 Un modelo también define un espacio de nombres para que el nombre completo de cada elemento de un modelo comience con el nombre del modelo.  
  
 Otros elementos del modelo también definen espacios de nombres. Por ejemplo, una operación pertenece al espacio de nombres definido por su clase principal, por lo que su nombre completo es como este `MyModel ::MyPackage ::MyClass ::MyOperation`. De la misma manera, una acción pertenece al espacio de nombres definido por su actividad principal.  
  
 Los paquetes son contenedores. Si mueve o elimina un paquete, también se mueven o eliminan las clases, los paquetes y otras cosas definidas dentro de este. Lo mismo puede decirse de otros elementos que definen los espacios de nombres.  
  
## <a name="Packages"></a> Crear y ver paquetes  
 Puede crear un paquete en un diagrama de clases UML o en el Explorador de modelos UML.  
  
#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>Para crear un paquete en un diagrama de clases UML  
  
1. Abra un diagrama de clases UML o cree uno nuevo.  
  
2. Haga clic en el **paquete** herramienta.  
  
3. Haga clic en cualquier parte del diagrama. Aparecerá una nueva forma de paquete.  
  
     Puede hacer clic en un paquete existente para anidar un paquete dentro de otro.  
  
4. Escriba un nombre nuevo para el paquete.  
  
#### <a name="to-create-a-package-in-uml-model-explorer"></a>Para crear un paquete en el Explorador de modelos UML  
  
1. Abra **Explorador de modelos UML**. En el **arquitectura** menú, elija **Windows**y, a continuación, haga clic en el **Explorador de modelos UML**.  
  
2. Haga clic con el botón secundario en un paquete o modelo al que desee agregar un nuevo paquete.  
  
   > [!NOTE]
   >  Puede anidar un paquete dentro de otro paquete.  
  
3. Seleccione **agregar** y, a continuación, haga clic en **paquete**.  
  
    Aparece un nuevo paquete en el modelo.  
  
4. Escriba un nombre nuevo para el paquete.  
  
   Si creó un paquete en el Explorador de modelos UML, puede mostrarlo en un diagrama de clases UML. También puede mostrar un paquete en más de un diagrama de clases UML.  
  
#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Para mostrar un paquete existente en un diagrama de clases UML  
  
- Arrastre el paquete desde el Explorador de modelos UML hasta el diagrama de clases.  
  
    > [!NOTE]
    >  Se crea una vista del paquete en este diagrama. No necesariamente mostrará todos los elementos que contiene el paquete. Para asegurarse de que ve todo el contenido de un paquete, véalo en el Explorador de modelos UML.  
  
## <a name="Elements"></a> Crear elementos del modelo dentro de paquetes  
 Hay cuatro maneras en que puede colocar elementos del modelo dentro de un paquete:  
  
- Agregar un nuevo elemento a un paquete en el Explorador de modelos UML.  
  
- Agregar clases y otros tipos a los paquetes en un diagrama de clases UML.  
  
- Establecer el **LinkedPackage** propiedad de un diagrama para que los nuevos elementos creados en el diagrama se colocan dentro del paquete especificado. Los diagramas de clases, los diagramas de componentes y los diagramas de casos de uso se pueden vincular a un paquete de esta manera.  
  
- Mover elementos dentro o fuera de un paquete en el Explorador de modelos UML.  
  
  Un elemento en un paquete aparece debajo del paquete en el Explorador de modelos UML y su nombre completo comienza con el nombre completo del paquete. Para ver el nombre completo de cualquier elemento, haga clic en el elemento y, a continuación, haga clic en **propiedades**. El **nombre completo** propiedad aparece en la **propiedades** ventana.  
  
#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>Para crear un elemento en un paquete del Explorador de modelos UML  
  
1. Abra **Explorador de modelos UML**. En el **vista** menú, elija **Other Windows**y, a continuación, haga clic en **Explorador de modelos UML**.  
  
2. Haga clic con el botón secundario en un paquete o modelo al que desee agregar un nuevo elemento.  
  
3. Seleccione **agregar**y, a continuación, haga clic en el tipo de elemento que desea agregar.  
  
     El nuevo elemento aparecerá debajo del paquete.  
  
4. Escriba un nombre para el nuevo elemento.  
  
    > [!NOTE]
    >  El nuevo elemento no aparece en ningún diagrama. Para crear una vista del nuevo elemento, puede arrastrarlo desde el Explorador de modelos UML a un diagrama. El diagrama debe ser un tipo que mostrará este tipo de elemento.  
  
#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>Para crear un elemento en un paquete de un diagrama de clases UML  
  
1. Abra un diagrama de clases en el que aparezca el paquete.  
  
    - Si aún no lo ha hecho, cree un paquete nuevo.  
  
    - Para que un paquete existente aparezca en un diagrama de clases, puede arrastrar el paquete desde **Explorador de modelos UML** al diagrama de clases.  
  
2. Haga clic en la herramienta para una clase, interfaz, enumeración o paquete.  
  
3. Haga clic en el paquete donde desea colocar el nuevo elemento.  
  
     El nuevo elemento aparecerá dentro del paquete.  
  
#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Para crear todos los elementos de un diagrama en un paquete especificado  
  
1. Si aún no lo ha hecho, cree el paquete.  
  
2. Abra un diagrama de componentes, un diagrama de casos de uso o un diagrama de clases UML.  
  
3. Abra las propiedades del diagrama. Haga clic en una parte en blanco del diagrama y, a continuación, haga clic en **propiedades**.  
  
4. En el **LinkedPackage** propiedad, elija el paquete que desea que contenga el contenido del diagrama.  
  
5. Cree nuevos elementos en el diagrama: Se colocarán en el paquete.  
  
    - El **nombre completo** de cada elemento comenzará con el nombre completo del paquete.  
  
    - En **Explorador de modelos UML**, cada elemento aparecerá en el paquete.  
  
## <a name="Moving"></a> Mover elementos dentro y fuera de los paquetes  
 Puede mover uno o varios elementos dentro o fuera de un paquete.  
  
 Si mueve un paquete, todo su contenido se mueve con él.  
  
#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Para mover un elemento dentro o fuera de un paquete  
  
- En el Explorador de modelos UML, arrastre el elemento dentro o fuera del árbol cuya raíz es el paquete.  
  
     El nombre completo del elemento cambiará para mostrar su nuevo paquete o modelo propietario.  
  
     \- o -  
  
- En un diagrama de clases, arrastre el elemento a una forma de paquete.  
  
     El nombre completo del elemento cambiará para mostrar su nuevo paquete propietario.  
  
    > [!NOTE]
    >  Si arrastra un elemento fuera de un paquete a una parte en blanco del diagrama, su paquete propietario no cambiará. Esto permite crear un diagrama que muestra los elementos de varios paquetes sin tener que mostrar los paquetes mismos.  
  
## <a name="Pasting"></a> Pegar elementos en un paquete  
 Puede pegar un elemento en un paquete. Si pega un grupo de elementos relacionados en un paquete, también se pegarán las relaciones entre ellos.  
  
#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>Para pegar elementos en un paquete de un diagrama de clases UML  
  
1. En un diagrama de clases UML, seleccione todos los elementos que desea copiar. Haga clic en uno de ellos y, a continuación, haga clic en **copia**.  
  
2. Haga clic en el paquete y, a continuación, haga clic en **pegar**.  
  
    > [!NOTE]
    >  El paquete puede estar en un diagrama diferente.  
  
## <a name="Import"></a> Importar relaciones entre paquetes  
 Puede definir una relación de importación entre paquetes, mediante el **importar** herramienta.  
  
 La importación significa que los elementos definidos en el paquete importado, que son los elementos en el extremo de flecha de la relación, también se definen de forma efectiva en el paquete de importación. Todos los elementos cuya visibilidad se define como **paquete** será visible también en el paquete de importación.  
  
 Evite crear bucles en las relaciones de importación.  
  
## <a name="References"></a> Referencias a uno Namespace a otro  
 Si desea hacer referencia a un elemento de un paquete de otro, debe usar el nombre completo del elemento.  
  
 Por ejemplo, suponga que el paquete `SalesCommon` define el tipo `CustomerAddress`. En otro paquete `RestaurantSales`, desea definir un tipo `MealOrder`, que tiene un atributo de tipo Dirección del cliente. Tiene dos opciones:  
  
- Especificar el tipo del atributo mediante el nombre completo `SalesCommon::CustomerAddress`. Debe hacer esto solo si `CustomerAddress` tiene su **visibilidad** propiedad establecida en **pública**.  
  
- Crear una relación de importación desde el paquete `RestaurantSales` al paquete `SalesCommon`. Puede usar `CustomerAddress` sin utilizar su nombre completo.  
  
## <a name="Properties"></a> Propiedades de paquetes  
 Cada paquete tiene las propiedades siguientes. Para ver las propiedades, haga clic en el paquete, en un diagrama o en el Explorador de modelos UML y, a continuación, haga clic en **propiedades**.  
  
|Propiedad|Valor predeterminado|Descripción|  
|--------------|-------------------|-----------------|  
|**Name**|(un nombre nuevo)|Nombre del paquete. Se puede cambiar tanto en el diagrama como en la ventana Propiedades.|  
|**Nombre completo**|*Contenedor* :: *nombre del paquete*|Nombre completo, precedido por el nombre del paquete o modelo que contiene este paquete. Para más información, consulte [Espacios de nombres](#Namespaces).|  
|**Perfiles**|(vacío)|Una lista de los perfiles vinculados a este paquete. Estos perfiles proporcionan estereotipos que se pueden aplicar a los elementos dentro del paquete. Para obtener más información, consulte [personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
|**Visibilidad**|**Public**|La visibilidad del paquete fuera de su paquete principal.|  
|**Los elementos de trabajo**|(vacío)|Una lista de elementos de trabajo vinculados. Para obtener más información, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|  
|**Ubicación de la definición**|(nombre)|El nombre de archivo donde se almacenan los detalles del paquete. Los archivos están dentro de la **ModelDefinition** carpeta del proyecto. Esta información puede ser útil con fines de control de código fuente.|  
|**Descripción**|(vacío)|Una descripción del paquete.|  
|**Estereotipos**|(vacío)|Estereotipos aplicados a este paquete. La lista de estereotipos disponibles está determinada por los perfiles que eligió para este paquete y los paquetes que lo contienen. Para obtener más información, consulte [personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
  
## <a name="how-packages-are-stored"></a>Cómo se almacenan los paquetes  
 Cuando se crea un nuevo paquete, un nuevo **.uml** archivo se crea en el **ModelDefinition** carpeta del proyecto. El modelo raíz, que también es un paquete, también se almacena en un **.uml** archivo.  
  
 Además, cada diagrama se almacena en dos archivos, uno que representa las formas del diagrama, y un **.layout** archivo que registra las posiciones de las formas.  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrama de clases de UML: Referencia](../modeling/uml-class-diagrams-reference.md)   
 [Diagrama de clases de UML: Directrices](../modeling/uml-class-diagrams-guidelines.md)   
 [Administrar modelos y diagramas con control de versiones](../modeling/manage-models-and-diagrams-under-version-control.md)
