---
title: Filtrar Crear una solución de lenguajes específicos de dominio
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01f229e3763777784fab193034eb79a643f5da13
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416197"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Filtrar Crear una solución de lenguajes específicos de dominio
Un lenguaje específico de dominio (DSL) se crea mediante el uso de una solución de Visual Studio especializada.

## <a name="prerequisites"></a>Requisitos previos

Puede iniciar este procedimiento, antes de instalar estos componentes:

- Programa para la mejora
- SDK de Visual Studio (instalado como parte de la **desarrollo de extensiones de Visual Studio** carga de trabajo)
- Modelar el SDK (se instala como un componente de Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Creación de una solución de lenguaje específico de dominio

1. Iniciar el Asistente de DSL creando un nuevo **Diseñador de lenguaje específico de dominio** proyecto.

   > [!NOTE]
   > Si es posible, el nombre que elija para el proyecto debe ser un objeto Visual válido C# identificador porque podría usarse para generar el código.

   ::: moniker range="vs-2017"

   ![Cuadro de diálogo para crear solución DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Elija una plantilla DSL.

    En el **seleccionar opciones de lenguaje específico de dominio** página, seleccione una de las plantillas de solución como **lenguaje mínimo**. Elija una plantilla que es similar a la línea ADSL que desea crear.

    Para obtener más información acerca de las plantillas de solución, consulte [elegir una plantilla de solución de lenguajes específicos de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Escriba una extensión de nombre de archivo el **extensión de archivo** página. Debe ser único en el equipo y en los equipos en los que desea instalar el DSL. Debería ver el mensaje **editores de Visual Studio ni las aplicaciones usan esta extensión**.

   -   Si ha utilizado la extensión de nombre de archivo anterior DSL experimental que no se han instalado completamente, puede desactivarlas alejar usando la **restablecer la instancia Experimental** herramienta, que puede encontrarse en el menú de Visual Studio SDK.

   -   Si otra extensión de Visual Studio que usa esta extensión de archivo se ha instalado completamente en el equipo, considere la posibilidad de desinstalarlo. En el **herramientas** menú, haga clic en **Administrador de extensiones**.

4. Inspeccione y, si es necesario ajustar, los campos en las páginas restantes del asistente. Cuando esté satisfecho con la configuración, haga clic en **finalizar**. Para obtener más información acerca de la configuración, consulte [páginas de asistente del Diseñador de DSL](#settings).

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
- [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
