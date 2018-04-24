---
title: 'Cómo: Crear soluciones de lenguajes específicos de dominio'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 955c8f7a6dbc55d61b1cba77f38b2d394742e49c
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Cómo: Crear soluciones de lenguajes específicos de dominio
Un lenguaje específico de dominio (DSL) se crea mediante especializada [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución.

## <a name="prerequisites"></a>Requisitos previos
 Antes de empezar este procedimiento, primero debe instalar estos componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|SDK de Visual Studio de visualización y modelado||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


## <a name="creating-a-domain-specific-language-solution"></a>Crear una solución de lenguaje específico de dominio

#### <a name="to-create-a-domain-specific-language-solution"></a>Para crear una solución de lenguaje específico de dominio

1.  Inicie al Asistente DSL.

    1.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

    2.  Aparecerá el cuadro de diálogo **Nuevo proyecto** .

    3.  En **tipos de proyecto**, expanda la **otros tipos de proyectos** nodo y haga clic en **extensibilidad**.

    4.  Haga clic en **Diseñador de lenguaje específico de dominio**.

    5.  En el **nombre** , escriba un nombre para la solución. Haga clic en **Aceptar**.

         El **Asistente del Diseñador de lenguaje específico de dominio** aparece.

        > [!NOTE]
        >  Si es posible, el nombre que escriba debe ser un identificador Visual C# válido, ya que podría utilizarse para generar el código.

     ![Cuadro de diálogo DSL crear](../modeling/media/create_dsldialog.png "Create_DSLDialog")

2.  Elija una plantilla DSL.

     En el **seleccionar opciones de lenguaje específico de dominio** , seleccione una de las plantillas de solución como **lenguaje mínimo**. Elija una plantilla que es similar a la línea ADSL que desea crear.

     Para obtener más información acerca de las plantillas de solución, vea [elegir una plantilla de solución de lenguaje específico de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

3.  Escriba una extensión de nombre de archivo el **extensión de archivo** página. Debe ser único en el equipo y en cualquier equipo en el que desea instalar el ADSL. Debería ver el mensaje **editores de Visual Studio ni las aplicaciones usan esta extensión**.

    -   Si ha usado la extensión de nombre de archivo en DSL experimental anterior que no se han instalado completamente, puede desactivarlas horizontal mediante el uso de la **restablecer la instancia Experimental** herramienta, que puede encontrarse en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] menú SDK.

    -   Si otro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión que utiliza esta extensión de archivo se ha instalado completamente en el equipo, considere la posibilidad de desinstalarlo. En el **herramientas** menú, haga clic en **Extension Manager**.

4.  Inspeccionar y, si es necesario ajustar, los campos en las páginas restantes del asistente. Cuando esté satisfecho con la configuración, haga clic en **finalizar**. Para obtener más información acerca de la configuración, consulte [páginas del Asistente de diseñador DSL](#settings).

     El asistente crea una solución que tiene dos proyectos, que se denominan **Dsl** y **DslPackage**.

    > [!NOTE]
    >  Si ve un mensaje que le avisa de no ejecutar plantillas de texto desde orígenes de confianza, haga clic en **Aceptar**. Puede establecer este mensaje no que aparezca de nuevo.

##  <a name="settings"></a> Las páginas del Asistente para el Diseñador de DSL
 Puede dejar algunos de los campos que no ha cambiado desde sus valores predeterminados. Sin embargo, asegúrese de que se establezca el campo de extensión de archivo.

### <a name="solution-settings-page"></a>Página de configuración de la solución
 **¿Qué plantilla desea basar su lenguaje específico del dominio en?**
Elija una plantilla que es similar a la línea ADSL que desea crear. Las diferentes plantillas proporcionan puntos de partida cómodos. Cuando se selecciona una plantilla de solución, el asistente muestra una descripción. Para obtener más información acerca de las plantillas de solución, vea [elegir una plantilla de solución de lenguaje específico de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **¿Qué desea el nombre de su lenguaje específico de dominio?**
El valor predeterminado es el nombre de la solución. Se genera el código de este valor. Debe ser válido como un nombre de clase de C#.

### <a name="file-extension-page"></a>Página de extensión de archivo
 **¿Qué extensión debe modelar usan los archivos?**
Escriba una nueva extensión de archivo.

 Compruebe que esta extensión de archivo no ya se ha registrado para su uso en este equipo, como se indica a continuación:

 Busque en **otras herramientas y aplicaciones registran para controlar esta extensión**. Si ve el mensaje **editores de Visual Studio ni las aplicaciones usan esta extensión**, a continuación, puede usar esta extensión de archivo.

 Si ve una lista de herramientas o paquetes, debe realizar una de las siguientes acciones:

-   Escriba una extensión de archivo diferente.

     \- o -

-   Restablecer el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instancia Experimental. Se eliminarán todos los lenguajes DSL que ya ha creado. En el **iniciar** menú, haga clic en **todos los programas**, **Microsoft Visual Studio 2010 SDK**, **herramientas**y, a continuación, **restablecer el Instancia de Microsoft Visual Studio 2010 Experimental**. Puede volver a generar los lenguajes DSL que desee volver a usar.

     \- o -

-   Si un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] las extensiones que utilicen esta extensión de archivo se ha instalado completamente en el equipo, desinstálelo. En el **herramientas** menú, haga clic en **Extension Manager**.

### <a name="product-settings-page"></a>Página de configuración del producto
 **¿Cuál es el nombre del producto al que pertenece el nuevo lenguaje específico de dominio?**
El valor predeterminado es el nombre DSL.

 Este valor se utiliza en el Explorador de Windows (o explorador de archivos) para describir los archivos que tienen esta extensión de archivo.

 **¿Qué es el nombre de la compañía a la que pertenece el producto?**
Nombre de su compañía.

 Este valor se incorpora a las propiedades de AssemblyInfo del paquete ADSL.

 **¿Qué es el espacio de nombres raíz para los proyectos de esta solución?**
El valor predeterminado es un nombre compuesto de su empresa y nombres de producto.

### <a name="signing-page"></a>Página firma
 **Crear un archivo de clave de nombre seguro** la opción predeterminada consiste en crear una nueva clave para firmar el ensamblado DSL.

 **Usar la clave de nombre seguro existente** Use esta opción si desea integrar el ADSL con otro ensamblado.

 Para obtener más información sobre nombres seguros, vea [crear y utilizar ensamblados](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
