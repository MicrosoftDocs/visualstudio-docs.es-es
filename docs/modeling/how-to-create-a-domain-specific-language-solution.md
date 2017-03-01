---
title: "Cómo: crear una solución de lenguaje específico de dominio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: b7c6f6f854e17e9b3b19f277d49674c311edb41b
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Cómo: Crear soluciones de lenguajes específicos de dominio
Un lenguaje específico de dominio (DSL) se crea mediante especializada [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Antes de empezar este procedimiento, primero debe instalar estos componentes:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|SDK de Visual Studio de visualización y modelado||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>Creación de una solución de lenguaje específico de dominio  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>Para crear una solución de lenguaje específico de dominio  
  
1.  Inicie al Asistente DSL.  
  
    1.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
    2.  Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
    3.  En **tipos de proyecto**, expanda la **otros tipos de proyectos** nodo y haga clic en **extensibilidad**.  
  
    4.  Haga clic en **Diseñador de lenguaje específico de dominio**.  
  
    5.  En el **nombre** , escriba un nombre para la solución. Haga clic en **Aceptar**.  
  
         El **Asistente del Diseñador de lenguaje específico de dominio** aparece.  
  
        > [!NOTE]
        >  Si es posible, el nombre que escriba debe ser un identificador Visual C# válido, porque se podría usar para generar el código.  
  
     ![Crear cuadro de diálogo DSL](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  Elija una plantilla DSL.  
  
     En el **seleccionar opciones de lenguaje específico de dominio** , seleccione una de las plantillas de solución como **lenguaje mínimo**. Elija una plantilla que sea similar a la DSL que desea crear.  
  
     Para obtener más información acerca de las plantillas de solución, consulte [elegir una plantilla de solución de lenguaje específico de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3.  Escriba una extensión de nombre de archivo el **extensión de archivo** página. Debe ser único en el equipo y en cualquier equipo en el que desea instalar el DSL. Debería ver el mensaje **ninguna aplicación o los editores de Visual Studio usan esta extensión**.  
  
    -   Si ha usado la extensión de nombre de archivo en DSL experimental anterior que no se han instalado completamente, puede desactivarlas horizontal mediante el uso de la **restablecer la instancia Experimental** herramienta, que se encuentra en la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] menú SDK.  
  
    -   Si otro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión que utiliza esta extensión de archivo se instala completamente en su equipo, considere la posibilidad de desinstalarlo. En el **herramientas** menú, haga clic en **Administrador de extensiones**.  
  
4.  Inspeccionar y, si es necesario ajustar, los campos en las páginas restantes del asistente. Cuando esté satisfecho con la configuración, haga clic en **finalizar**. Para obtener más información acerca de la configuración, consulte [páginas de asistente del Diseñador de DSL](#settings).  
  
     El asistente crea una solución que tiene dos proyectos, que se denominan **Dsl** y **DslPackage**.  
  
    > [!NOTE]
    >  Si ve un mensaje que le avisa de no ejecutar plantillas de texto desde orígenes de confianza, haga clic en **Aceptar**. Puede establecer este mensaje no aparezca de nuevo.  
  
##  <a name="a-namesettingsa-the-dsl-designer-wizard-pages"></a><a name="settings"></a>Las páginas del Asistente para el Diseñador de DSL  
 Puede dejar algunos de los campos no cambios desde sus valores predeterminados. Sin embargo, asegúrese de que establece el campo de extensión de archivo.  
  
### <a name="solution-settings-page"></a>Página de configuración de la solución  
 **¿Qué plantilla desea basar su lenguaje específico de dominio?**  
 Elija una plantilla que sea similar a la DSL que desea crear. Las diferentes plantillas proporcionan puntos de partida cómodos. Al seleccionar una plantilla de solución, el asistente muestra una descripción. Para obtener más información acerca de las plantillas de solución, consulte [elegir una plantilla de solución de lenguaje específico de dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 **¿Qué desea el nombre de su lenguaje específico de dominio?**  
 El valor predeterminado es el nombre de la solución. Se genera el código de este valor. Debe ser válido, como un nombre de clase de C#.  
  
### <a name="file-extension-page"></a>Página de extensión de archivo  
 **¿Debe modelar qué extensión de archivos de uso?**  
 Escriba una nueva extensión de archivo.  
  
 Compruebe que esta extensión de archivo aún no se ha registrado para su uso en este equipo, como sigue:  
  
 Busque en **otras herramientas y aplicaciones que se registran para administrar esta extensión**. Si ve el mensaje **ninguna aplicación o los editores de Visual Studio usan esta extensión**, puede usar esta extensión de archivo.  
  
 Si ve una lista de paquetes o herramientas, debe realizar una de las siguientes acciones:  
  
-   Escriba una extensión de archivo diferente.  
  
     \- o -  
  
-   Restablecer el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instancia Experimental. Se eliminarán todos los DSL que ya ha creado. En el **iniciar** menú, haga clic en **todos los programas**, **Microsoft Visual Studio 2010 SDK**, **herramientas**y, a continuación, **restablecer la instancia de Microsoft Visual Studio 2010 Experimental**. Puede volver a generar los lenguajes DSL que desee volver a usar.  
  
     \- o -  
  
-   Si un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión que utiliza esta extensión de archivo se instala completamente en su equipo, desinstálelo. En el **herramientas** menú, haga clic en **Administrador de extensiones**.  
  
### <a name="product-settings-page"></a>Página de configuración del producto  
 **¿Qué es el nombre del producto al que pertenece el nuevo lenguaje específico de dominio?**  
 El valor predeterminado es el nombre DSL.  
  
 Este valor se utiliza en el Explorador de Windows (o explorador de archivos) para describir los archivos que tienen esta extensión de archivo.  
  
 **¿Qué es el nombre de la compañía a la que pertenece el producto?**  
 Nombre de su compañía.  
  
 Este valor se incorpora las propiedades AssemblyInfo de su paquete DSL.  
  
 **¿Qué es el espacio de nombres raíz para los proyectos de esta solución?**  
 El valor predeterminado es un nombre compuesto de su empresa y los nombres de producto.  
  
### <a name="signing-page"></a>Página firma  
 **Crear un archivo de clave de nombre seguro**  
 La opción predeterminada es crear una nueva clave para firmar el ensamblado DSL.  
  
 **Usar la clave de nombre seguro existente**  
 Utilice esta opción si desea integrar su DSL con otro ensamblado.  
  
 Para obtener más información sobre nombres seguros, vea [crear y utilizar ensamblados](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Vea también  
 [Cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Glosario de herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

