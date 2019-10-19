---
title: Definir e instalar una extensión de modelado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66a9cdab1284d015e2ea76162d240b6a1232d90f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669914"
---
# <a name="define-and-install-a-modeling-extension"></a>Definir e instalar una extensión de modelado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede definir extensiones para diagramas de modelado. De este modo, puede adaptar los diagramas y modelos a sus propias necesidades. Puede definir, por ejemplo, comandos de menú, perfiles de UML, restricciones de validación y elementos de cuadros de herramientas. Puede definir varios componentes en una única extensión. También puede distribuir estas extensiones a otros usuarios de Visual Studio en forma de [extensión de integración de Visual Studio (VSIX)](http://go.microsoft.com/fwlink/?LinkId=160780). Puede crear una extensión VSIX usando un proyecto VSIX en Visual Studio.

## <a name="requirements"></a>Requisitos
 Vea [Requisitos](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-modeling-extension-solution"></a>Crear una solución de extensión de modelado
 Para definir una extensión de modelado, debe crear una solución que contenga estos proyectos:

- Un proyecto de Extensión de integración de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). De este modo, se genera un archivo que actúa como instalador de los componentes de la extensión.

- Un proyecto de biblioteca de clases, necesario para los componentes que contienen el código del programa.

  Si desea realizar una extensión que tenga diversos componentes, puede desarrollarlos en una única solución. Solo se necesita un proyecto VSIX.

  Los componentes que no necesitan código, como los elementos de cuadro de herramientas personalizados y los perfiles UML personalizados, pueden agregarse directamente al proyecto VSIX sin usar proyectos de biblioteca de clases independientes. Los componentes que requieren código del programa, se definen más fácilmente en un proyecto de biblioteca de clases independiente. Entre los componentes que requieren código se incluyen los controladores de gestos, los comandos de menú y el código de validación.

#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Para crear un proyecto de biblioteca de clases para los comandos de menú, los controladores de gestos o la validación

1. En el menú **Archivo** , elija **Nuevo**, **Proyecto**.

2. En **Plantillas instaladas**, seleccione **Visual C#** o **Visual Basic**y, a continuación, elija **Biblioteca de clases**.

#### <a name="to-create-a-vsix-project"></a>Para crear un proyecto de VSIX

1. Si está creando un componente con código, es más fácil crear primero el proyecto de biblioteca de clases. Va a agregar su código a ese proyecto.

2. Crear un proyecto de VSIX.

    1. En el **Explorador de soluciones**, en el menú contextual de la solución, elija **Agregar**, **Nuevo proyecto**.

    2. En **Plantillas instaladas**, expanda **Visual C#** o **Visual Basic**y, a continuación, seleccione **Extensibilidad**. En la columna central, elija **Proyecto VSIX**.

3. Establezca el proyecto VSIX como proyecto de inicio de la solución.

    - En el Explorador de soluciones, en el menú contextual del proyecto VSIX, elija **Establecer como proyecto de inicio**.

4. Abra **source.extension.vsixmanifest**. El archivo se abre en el editor de manifiestos.

5. En la pestaña **Metadatos** , establezca el nombre y los campos descriptivos de VSIX.

6. En la pestaña **Destinos de instalación** , elija **Nuevo** y establezca las versiones de Visual Studio como destinos.

7. En la pestaña **Activos** , agregue los componentes a la extensión de Visual Studio.

    1. Elija **Nuevo**.

    2. Para un componente con código, establezca estos campos en el cuadro de diálogo **Agregar nuevo activo** :

        |||
        |-|-|
        |**Escribir**  =|**Microsoft. VisualStudio. MefComponent**|
        |**Source** =|**Proyecto en la solución actual**|
        |@No__t_1 del **proyecto**|*Su proyecto de biblioteca de clases*|
        |**Inserte en esta carpeta**  =|*vacía*|

         Para otros tipos de componentes, vea los vínculos de la sección siguiente.

## <a name="developing-the-component"></a>Desarrollar el componente
 Para cada componente, por ejemplo un comando de menú o un controlador de gestos, debe definir un controlador independiente. Puede colocar varios controladores en el mismo proyecto de biblioteca de clases. En la siguiente tabla se resumen los diferentes tipos de controlador.

|Tipo de extensión|Tema|Cómo se declara normalmente cada componente|
|--------------------|-----------|----------------------------------------------|
|Comando de menú|[Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|
|Arrastrar y colocar o hacer doble clic|[Definir un controlador de gestos en un diagrama de modelado](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|
|Restricción de validación|[Definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|
|Controlador de eventos de vínculo de elemento de trabajo|[Definir un controlador de vínculos de elementos de trabajo](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|
|Perfil UML|[Definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md)|(Por definir)|
|Elemento de cuadro de herramientas|[Definir un elemento personalizado en un cuadro de herramientas de modelado](../modeling/define-a-custom-modeling-toolbox-item.md)|(Por definir)|

## <a name="running-an-extension-during-its-development"></a>Ejecutar una extensión durante su desarrollo

#### <a name="to-run-an-extension-during-its-development"></a>Para ejecutar una extensión durante su desarrollo

1. En el menú [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **Depurar** , elija **Start Depurarging**.

     El proyecto se compila y se inicia una nueva instancia de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] en modo experimental.

    - Como alternativa, puede elegir **Iniciar sin depurar**. Esto reduce el tiempo que se tarda en iniciar el programa.

2. Cree o abra un proyecto de modelado en la instancia experimental de Visual Studio y cree o abra un diagrama.

     La extensión se cargará y se ejecutará.

3. Si usó **Iniciar sin depurar** pero desea utilizar el depurador, vuelva a la instancia principal de Visual Studio. En el menú **Depurar** , haga clic en **Asociar al proceso**. En el cuadro de diálogo, seleccione la instancia experimental de Visual Studio, que tiene el nombre de programa **devenv**.

## <a name="Installing"></a>Instalación y desinstalación de una extensión
 Realice los pasos siguientes para ejecutar la extensión en la instancia principal de Visual Studio en su propio equipo o en otros equipos.

1. En el equipo, busque el archivo **.vsix** que el proyecto de extensión compiló.

    1. En el **Explorador de soluciones**, en el menú contextual del proyecto, elija **Abrir carpeta en el Explorador de Windows**.

    2. Busque el archivo **bin \\ \* \\** _YourProject_ **. vsix**

2. Copie el archivo **.vsix** en el equipo de destino en el que desea instalar la extensión. Puede tratarse de su propio equipo o de otro.

    - El equipo de destino debe tener una de las ediciones de Visual Studio que se especificó en la pestaña **Destino de la instalación** de **source.extension.vsixmanifest**.

3. En el equipo de destino, abra el archivo **.vsix** , por ejemplo, haciendo doble clic en él.

     El**Instalador de extensiones de Visual Studio** se abre e instala la extensión.

4. Inicie o reinicie Visual Studio.

#### <a name="to-uninstall-an-extension"></a>Para desinstalar una extensión

1. En el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**

2. Expanda **Extensiones instaladas**.

3. Seleccione la extensión y, a continuación, haga clic **Desinstalar**.

   En contadas ocasiones, una extensión defectuosa no se carga y crea un informe en la ventana de error, aunque no aparece en el Administrador de extensiones. En ese caso, puede quitar la extensión eliminando el archivo de la siguiente ubicación en la que *% LocalAppData%* suele \\ ser el nombre de*usuario* *\AppData\Local:*

   *% LocalAppData%* **\Microsoft\VisualStudio \\ [versión] \Extensions**

## <a name="see-also"></a>Vea también
 [Definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md) [definir un elemento del cuadro de herramientas de modelado personalizado](../modeling/define-a-custom-modeling-toolbox-item.md) [definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md) [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
