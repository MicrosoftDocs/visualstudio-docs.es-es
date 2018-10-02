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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8684f85c7e5ccb8b4ca93ccc51a24c17ac40f633
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859619"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Cómo: Crear soluciones de lenguajes específicos de dominio
Un lenguaje específico de dominio (DSL) se crea mediante el uso de una solución de Visual Studio especializada.

## <a name="prerequisites"></a>Requisitos previos
 Antes de que puede iniciar este procedimiento, primero debe instalar estos componentes:

|||
|-|-|
|Programa para la mejora|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|SDK de Visual Studio de visualización y modelado||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


## <a name="creating-a-domain-specific-language-solution"></a>Creación de una solución de lenguaje específico de dominio

#### <a name="to-create-a-domain-specific-language-solution"></a>Para crear una solución de lenguaje específico de dominio

1.  Inicie al Asistente DSL.

    1.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

    2.  Aparecerá el cuadro de diálogo **Nuevo proyecto** .

    3.  En **tipos de proyecto**, expanda el **otros tipos de proyectos** nodo y haga clic en **extensibilidad**.

    4.  Haga clic en **Diseñador de lenguaje específico de dominio**.

    5.  En el **nombre** , escriba un nombre para la solución. Haga clic en **Aceptar**.

         El **Asistente del Diseñador de lenguaje específico de dominio** aparece.

        > [!NOTE]
        >  Si es posible, el nombre que escriba debe ser un identificador Visual C# válido, porque podría usarse para generar el código.

     ![Cuadro de diálogo para crear solución DSL](../modeling/media/create_dsldialog.png)

2.  Elija una plantilla DSL.

     En el **seleccionar opciones de lenguaje específico de dominio** página, seleccione una de las plantillas de solución como **lenguaje mínimo**. Elija una plantilla que es similar a la línea ADSL que desea crear.

     Para obtener más información acerca de las plantillas de solución, consulte [elegir una plantilla de solución de lenguajes específicos de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

3.  Escriba una extensión de nombre de archivo el **extensión de archivo** página. Debe ser único en el equipo y en los equipos en los que desea instalar el DSL. Debería ver el mensaje **editores de Visual Studio ni las aplicaciones usan esta extensión**.

    -   Si ha utilizado la extensión de nombre de archivo anterior DSL experimental que no se han instalado completamente, puede desactivarlas alejar usando la **restablecer la instancia Experimental** herramienta, que puede encontrarse en el menú de Visual Studio SDK.

    -   Si otra extensión de Visual Studio que usa esta extensión de archivo se ha instalado completamente en el equipo, considere la posibilidad de desinstalarlo. En el **herramientas** menú, haga clic en **Administrador de extensiones**.

4.  Inspeccione y, si es necesario ajustar, los campos en las páginas restantes del asistente. Cuando esté satisfecho con la configuración, haga clic en **finalizar**. Para obtener más información acerca de la configuración, consulte [páginas de asistente del Diseñador de DSL](#settings).

     El asistente crea una solución que tiene dos proyectos, que se denominan **Dsl** y **DslPackage**.

    > [!NOTE]
    >  Si ve un mensaje que no le avisa para ejecutar las plantillas de texto de fuentes no confiables, haga clic en **Aceptar**. Puede establecer este mensaje no se mostrarán de nuevo.

## <a name="settings"></a> Las páginas del Asistente para el Diseñador de DSL
 Puede dejar algunos de los campos que no ha cambiado desde sus valores predeterminados. Sin embargo, asegúrese de establecer el campo de extensión de archivo.

### <a name="solution-settings-page"></a>Página de configuración de la solución
 **¿Qué plantilla desea basar su lenguaje específico de dominio?**
Elija una plantilla que es similar a la línea ADSL que desea crear. Las diferentes plantillas que proporcionan puntos de partida cómodos. Cuando se selecciona una plantilla de solución, el asistente muestra una descripción. Para obtener más información acerca de las plantillas de solución, consulte [elegir una plantilla de solución de lenguajes específicos de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **¿Qué desea el nombre de su lenguaje específico de dominio?**
El valor predeterminado es el nombre de la solución. Se genera el código de este valor. Debe ser válida como un nombre de clase de C#.

### <a name="file-extension-page"></a>Página de extensión de archivo
 **¿Qué extensión debe modelar archivos usan?**
Escriba una nueva extensión de archivo.

 Compruebe que esta extensión de archivo aún no se ha registrado para su uso en este equipo, como se indica a continuación:

 Mire en **otras herramientas y aplicaciones registran para controlar esta extensión**. Si ve el mensaje **editores de Visual Studio ni las aplicaciones usan esta extensión**, puede usar esta extensión de archivo.

 Si ve una lista de herramientas o paquetes, debe realizar una de las siguientes acciones:

-   Escriba una extensión de archivo diferente.

     \- o -

-   Restablecer la instancia Experimental de Visual Studio. Se eliminarán todos los DSL que se hayan creado anteriormente. En el **iniciar** menú, haga clic en **todos los programas**, **Microsoft Visual Studio 2010 SDK**, **herramientas**y, a continuación, **restablecer el Instancia de Microsoft Visual Studio 2010 Experimental**. Puede volver a generar los lenguajes DSL que desee volver a usar.

     \- o -

-   Si una extensión de Visual Studio que usa esta extensión de archivo se ha instalado completamente en el equipo, desinstálelo. En el **herramientas** menú, haga clic en **Administrador de extensiones**.

### <a name="product-settings-page"></a>Página de configuración del producto
 **¿Qué es el nombre del producto al que pertenece el nuevo lenguaje específico de dominio?**
El valor predeterminado es el nombre DSL.

 Este valor se usa en el Explorador de Windows (o explorador de archivos) para describir los archivos que tienen esta extensión de archivo.

 **¿Qué es el nombre de la compañía que pertenece el producto?**
Nombre de su empresa.

 Este valor se incorpora en las propiedades de AssemblyInfo de su paquete DSL.

 **¿Qué es el espacio de nombres raíz para los proyectos de esta solución?**
El valor predeterminado es un nombre compuesto de su empresa y los nombres de producto.

### <a name="signing-page"></a>Página firma
 **Crear un archivo de clave de nombre seguro** la opción predeterminada es crear una nueva clave para firmar el ensamblado DSL.

 **Usar la clave de nombre seguro existente** Use esta opción si desea integrar su DSL con otro ensamblado.

 Para obtener más información acerca de nombres seguros, vea [crear y utilizar ensamblados](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Glosario de las herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
