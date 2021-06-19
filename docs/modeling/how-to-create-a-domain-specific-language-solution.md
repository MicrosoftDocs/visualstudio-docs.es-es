---
title: 'Cómo: Crear soluciones de lenguajes específicos de dominio'
description: Obtenga información sobre cómo crear un lenguaje específico de dominio (DSL) mediante una solución de Visual Studio especializada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ce03349a5179e8dd78220fffd1ff6b21d1a3b495
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387325"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Cómo: Crear soluciones de lenguajes específicos de dominio
Un lenguaje específico de dominio (DSL) se crea mediante una solución de Visual Studio especializada.

## <a name="prerequisites"></a>Requisitos previos

Para poder iniciar este procedimiento, instale estos componentes:

- Programa para la mejora
- Visual Studio SDK (instalado como parte de la carga de trabajo de Visual Studio **desarrollo de extensiones)**
- SDK de modelado (instalado como componente Visual Studio modelo)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Crear una solución Domain-Specific language

1. Inicie el Asistente para DSL mediante la creación de **Diseñador de lenguaje específico de dominio** proyecto.

   > [!NOTE]
   > Preferiblemente, el nombre que elija para el proyecto debe ser un identificador válido de Visual C# porque podría usarse para generar código.

   ::: moniker range="vs-2017"

   ![Cuadro de diálogo para crear solución DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Elija una plantilla dsl.

    En la **página Seleccionar Domain-Specific idioma,** seleccione una de las plantillas de solución, como **Lenguaje mínimo.** Elija una plantilla similar al DSL que desea crear.

    Para obtener más información sobre las plantillas de solución, vea [Elección de una Domain-Specific de solución de lenguaje.](../modeling/choosing-a-domain-specific-language-solution-template.md)

3. Escriba una extensión de nombre de archivo en la **página Extensión de** archivo. Debe ser único en el equipo y en los equipos en los que quiera instalar el DSL. Debería ver el mensaje **No applications or Visual Studio editors use esta extensión**.

   - Si ha usado la extensión de nombre de archivo en las DSL experimentales anteriores que no se han instalado por completo, puede borrarlas mediante la herramienta Restablecer la instancia **experimental,** que se puede encontrar en el menú del SDK de Visual Studio.

   - Si otra Visual Studio que usa esta extensión de archivo se ha instalado por completo en el equipo, considere la posibilidad de desinstalarla. En el menú **Herramientas,** haga clic en **Administrador de extensiones.**

4. Inspeccione y, si es necesario, ajuste los campos de las páginas restantes del asistente. Cuando esté satisfecho con la configuración, haga clic en **Finalizar.** Para obtener más información sobre la configuración, vea [Diseñador DSL páginas del Asistente para aplicaciones](#settings).

    El asistente crea una solución que tiene dos proyectos, denominados **Dsl** y **DslPackage.**

   > [!NOTE]
   > Si ve un mensaje que le avisa de que no debe ejecutar plantillas de texto desde orígenes que no son de confianza, haga clic en **Aceptar.** Puede establecer este mensaje para que no aparezca de nuevo.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a> Páginas del Asistente para Diseñador DSL de aplicaciones
 Puede dejar varios de los campos sin cambios con respecto a sus valores predeterminados. Sin embargo, asegúrese de establecer el campo Extensión de archivo.

### <a name="solution-settings-page"></a>Página Configuración de la solución
 **¿En qué plantilla desea basar el lenguaje específico del dominio?**
Elija una plantilla similar al DSL que desea crear. Las distintas plantillas proporcionan puntos de partida prácticos. Al seleccionar una plantilla de solución, el asistente muestra una descripción. Para obtener más información sobre las plantillas de solución, vea [Elección de una Domain-Specific de solución de lenguaje.](../modeling/choosing-a-domain-specific-language-solution-template.md)

 **¿Cómo quiere dar nombre al lenguaje específico del dominio?**
El valor predeterminado es el nombre de la solución. El código se genera a partir de este valor. Debe ser válido como nombre de clase de C#.

### <a name="file-extension-page"></a>Página Extensión de archivo
 **¿Qué extensión deben usar los archivos de modelo?**
Escriba una nueva extensión de archivo.

 Compruebe que esta extensión de archivo aún no se ha registrado para su uso en este equipo, como se muestra a continuación:

 Busque en **Otras herramientas y aplicaciones registradas para controlar esta extensión.** Si ve el mensaje **No hay aplicaciones ni editores** Visual Studio esta extensión , puede usar esta extensión de archivo.

 Si ve una lista de herramientas o paquetes, debe realizar una de las siguientes acciones:

- Escriba otra extensión de archivo.

     \- O bien

- Restablezca la Visual Studio experimental. Esto anulará el registro de todas las DSL que haya creado previamente. En el **menú** Inicio , haga clic en **Todos** los programas , **Microsoft Visual Studio SDK de 2010** **,** Herramientas y, a continuación, restablecer **la instancia experimental de Microsoft Visual Studio 2010**. Puede volver a generar cualquier otra DSL que quiera usar de nuevo.

     \- O bien

- Si una Visual Studio que usa esta extensión de archivo se ha instalado completamente en el equipo, desinstálela. En el menú **Herramientas,** haga clic en **Administrador de extensiones.**

### <a name="product-settings-page"></a>Página Configuración del producto
 **¿Cuál es el nombre del producto al que pertenece el nuevo lenguaje específico del dominio?**
El valor predeterminado es el nombre dsl.

 Este valor se usa en Explorador de Windows (o Explorador de archivos) para describir los archivos que tienen esta extensión de archivo.

 **¿Cuál es el nombre de la empresa a la que pertenece el producto?**
Nombre de la empresa.

 Este valor se incorpora a las propiedades AssemblyInfo del paquete DSL.

 **¿Cuál es el espacio de nombres raíz para los proyectos de esta solución?**
El valor predeterminado es un nombre compuesto por los nombres de empresa y producto.

### <a name="signing-page"></a>Página de firma
 **Creación de un archivo de clave de nombre segura** La opción predeterminada es crear una nueva clave para firmar el ensamblado DSL.

 **Uso de la clave de nombre segura existente** Use esta opción si desea integrar el DSL con otro ensamblado.

 Para obtener más información sobre la nomenclatura segura, vea [Creating and Using Strong-Named Assemblies](/dotnet/standard/assembly/create-use-strong-named).

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))