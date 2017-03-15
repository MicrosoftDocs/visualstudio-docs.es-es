---
title: "C&#243;mo: Crear un control Toolbox que use formularios Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Control Toolbox"
  - "winforms"
  - "toolbox"
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# C&#243;mo: Crear un control Toolbox que use formularios Windows Forms
La plantilla del control Toolbox de Windows Forms que se incluye en [!INCLUDE[vssdk_dev11_long](../misc/includes/vssdk_dev11_long_md.md)] le permite crear controles de formularios Windows Forms que se agregan automáticamente a **Toolbox** cuando se instala la extensión. En este tema se muestra cómo usar la plantilla para crear un control **Toolbox**, que se puede distribuir a otros usuarios.  
  
> [!NOTE]
>  Para obtener información sobre cómo descargar Visual Studio SDK, vea [Extensión de Visual Studio](http://go.microsoft.com/fwlink/?linkid=121964) en el sitio web de MSDN.  
  
## Crear un control Toolbox  
 Utilice la plantilla de control Toolbox de Windows Forms para crear el proyecto y, a continuación, cree una interfaz de usuario \(IU\) en el diseñador.  
  
#### Para crear un proyecto de Control de cuadro de herramientas de Windows Forms  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en **Plantillas instaladas**, haga clic en el nodo para elegir su lenguaje de programación preferido y luego haga clic en **Extensibilidad**. En la lista de tipos de proyecto, seleccione **Control Toolbox de Windows Forms**.  
  
3.  En el cuadro **Nombre**, escriba el nombre que desea utilizar para el proyecto. Haga clic en **Aceptar**.  
  
     Visual Studio crea una solución que contiene un control de usuario, un atributo para colocar el control en el **Cuadro de herramientas**, y el manifiesto de VSIX para la implementación.  
  
#### Para compilar la interfaz de usuario del control  
  
1.  En el **Explorador de soluciones**, haga doble clic en ToolboxControl.cs para abrirlo en el diseñador.  
  
2.  Desde el **Cuadro de herramientas**, arrastre los controles que desee a la superficie de diseño y organícelos según su diseño.  
  
3.  En la ventana **Propiedades**, establezca las propiedades públicas en el control de usuario y en los controles secundarios.  
  
## Codificación del control  
 De forma predeterminada, el control aparecerá en el **Cuadro de herramientas** como **ToolboxControl1** en un grupo de elementos de **Cuadro de herramientas** que tenga el mismo nombre que la solución. Puede cambiar estos nombres en el archivo ToolboxControl.cs.  
  
#### Para codificar el control  
  
1.  En el **Explorador de soluciones**, haga clic en ToolboxControl.cs y luego en **Ver código** para abrir el archivo en la vista de código.  
  
2.  En la definición de la clase parcial que implementa el control, haga clic con el botón secundario en el nombre de clase, haga clic en **Refactorizar**, y luego haga clic en **Cambiar nombre**. Cambie el nombre de la clase al nombre que desee que se muestre en el **Cuadro de herramientas** cuando se instale el control.  
  
3.  Justo encima de la definición de clase, en la declaración de atributos `ProvideToolboxControl`, cambie el valor del primer parámetro al nombre del grupo de elementos que va a hospedar el control en el **Cuadro de herramientas**.  
  
     El ejemplo siguiente muestra el atributo `ProvideToolboxControl` y la definición de clase ajustada para un control denominado `Counter` en el grupo de elementos `General`.  
  
     [!code-cs[ToolboxControlWinForms#07](../misc/codesnippet/CSharp/how-to-create-a-toolbox-control-that-uses-windows-forms_1.cs)]  
  
4.  Implemente las propiedades, métodos y eventos del control.  
  
## Compilación, prueba e implementación  
 Al presionar F5, se compila el proyecto, lo que incluye un archivo de implementación .vsix, y se abre una segunda instancia de Visual Studio con el control instalado en el **Cuadro de herramientas**.  
  
#### Para compilar y probar el control  
  
1.  Presione F5.  
  
2.  En la nueva instancia de Visual Studio, cree un proyecto de aplicación de Windows Forms.  
  
3.  Busque el control en el **Cuadro de herramientas** y arrástrelo a la superficie de diseño.  
  
4.  En la ventana **Propiedades**, compruebe que las propiedades aparecen como se esperaba.  
  
5.  Agregue cualquier código o los controles adicionales necesarios para probar los métodos y eventos.  
  
6.  Presione F5 para abrir la aplicación de Windows Forms.  
  
7.  Compruebe que las propiedades, métodos y eventos del control se comportan como se esperaba.  
  
#### Para implementar el control  
  
1.  Después de compilar el proyecto probado, abra la carpeta \\bin\\debug\\ del proyecto en el Explorador de archivos y busque el archivo .vsix.  
  
2.  Cargue el archivo .vsix en una red o en un sitio web.  
  
     Si va a cargar el archivo en el sitio web de la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), otros usuarios pueden usar **Administrador de extensiones** en Visual Studio para buscar el control e instalarlo.  
  
## Vea también  
 [Crear un Control de cuadro de herramientas WPF](../extensibility/creating-a-wpf-toolbox-control.md)