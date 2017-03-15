---
title: "Tutorial: Extensi&#243;n de paquetes VSPackage administrados mediante la automatizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paquetes VSPackage administrados, extender mediante automatización"
  - "automatización [SDK de Visual Studio], tutoriales"
  - "automatización [SDK de Visual Studio], paquetes VSPackage administrados"
ms.assetid: 7fd2000b-8ec3-4d83-b169-d38008fb57ee
caps.latest.revision: 35
caps.handback.revision: 35
manager: "douge"
---
# Tutorial: Extensi&#243;n de paquetes VSPackage administrados mediante la automatizaci&#243;n
En este tutorial se muestra cómo usar la automatización para crear un VSPackage administrado que manipule el entorno de desarrollo integrado \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Debe crear un VSPackage administrado de ejemplo y, después, usar los métodos de automatización en el VSPackage resultante para mostrar las propiedades de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en la Ventana de **salida**.  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Ubicaciones de la plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto de paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes en el cuadro de diálogo **Nuevo proyecto**:  
  
1.  En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2.  En Extensibilidad de C\#. El lenguaje predeterminado del proyecto es C\#.  
  
3.  En Extensibilidad de Otros tipos de proyectos. El lenguaje predeterminado del proyecto es C\+\+.  
  
### Para crear un VSPackage administrado  
  
1.  Cree un proyecto de paquete de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] denominado `Auto`.  
  
     Para obtener más información sobre cómo crear un VSPackage administrado, consulte [Tutorial: Crear un comando de menú mediante la plantilla de paquete de Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  En la página **Seleccione un lenguaje de programación**, establezca el lenguaje en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
3.  Mantenga los valores predeterminados de la página **Información básica de VSPackage**.  
  
4.  En la página **Seleccionar opciones del paquete de VS**, active la casilla **Comando de menú**.  
  
5.  En la página **Opciones de comando**, cambie el valor de **Nombre de comando** a `Auto`.  
  
6.  Haga clic en el botón **Finalizar**.  
  
     La plantilla genera un proyecto administrado denominado Auto.  
  
7.  Compile la solución y compruebe que se compila sin errores.  
  
### Para llamar al modelo de automatización  
  
1.  En el **Explorador de soluciones**, haga clic en el nodo de proyecto Auto y, después, haga clic en **Agregar**, **Referencia**.  
  
2.  En la pestaña **.NET** del cuadro de diálogo **Referencia**, haga doble clic en **EnvDTE**.  
  
     Se agrega una referencia al espacio de nombres de automatización EnvDTE.  
  
3.  En el archivo AutoPackage, agregue la siguiente referencia de espacio de nombres.  
  
     [!code-cs[VSSDKAuto#1](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_1.cs)]
     [!code-vb[VSSDKAuto#1](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_1.vb)]  
  
4.  En el archivo AutoPackage, reemplace el cuerpo del método `MenuItemCallback` por las siguientes líneas:  
  
     [!code-cs[VSSDKAuto#2](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_2.cs)]
     [!code-vb[VSSDKAuto#2](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_2.vb)]  
  
 Este código llama a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener un objeto de automatización <xref:EnvDTE.DTE> que representa el IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. El código de automatización de `MenuItemCallback` crea un nuevo panel en la Ventana de **salida** denominado **Test**. El nombre y la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se escriben en el nuevo panel **Salida**.  
  
1.  Compile e inicie el proyecto Auto en modo de depuración presionando F5.  
  
     Se inicia la compilación experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp\).  
  
    > [!NOTE]
    >  Ambas versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] están abiertas en este momento.  
  
2.  En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp, en el menú **Herramientas**, haga clic en **Auto**.  
  
     Un nuevo panel denominado **Test** se abre en la Ventana de **salida** y muestra lo siguiente:  
  
    ```  
    Name is Microsoft Visual Studio Version is x.xx  
    ```  
  
     Donde x.xx es el número de versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] más reciente.  
  
     Para obtener más información acerca de los ejemplos de automatización, consulte los [ejemplos de automatización de Visual Studio](http://www.microsoft.com/downloads/details.aspx?familyid=3ff9c915-30e5-430e-95b3-621dccd25150&displaylang=en).  
  
## Vea también  
 [Ampliar el entorno de Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)