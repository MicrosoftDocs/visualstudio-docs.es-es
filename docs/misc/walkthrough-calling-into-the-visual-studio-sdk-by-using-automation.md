---
title: "Tutorial: llamadas al SDK de Visual Studio mediante automatizaci&#243;n | Microsoft Docs"
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
  - "tutoriales [SDK de Visual Studio], llamadas con automatización"
ms.assetid: ca4dab48-632c-4c2a-8c84-57c027e37987
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Tutorial: llamadas al SDK de Visual Studio mediante automatizaci&#243;n
En este tutorial se muestra cómo crear un complemento de Visual Studio que consuma un servicio de Visual Studio. El complemento que cree obtiene un proveedor de servicios y lo usa para obtener un servicio. Puede utilizar esta misma técnica para obtener cualquier servicio de Visual Studio ofrecido. Para más información sobre los servicios y proveedores de servicios, consulte [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md). Los procedimientos siguientes muestran cómo crear un complemento y después obtener un servicio desde el complemento.  
  
## Crear un complemento  
 En esta sección, creará un complemento de Visual Studio con la plantilla de proyecto de complemento de Visual Studio.  
  
#### Para crear un complemento  
  
1.  Cree un nuevo proyecto de Visual Studio \(**Archivo\/Nuevo\/Proyecto**\).  
  
2.  En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Otros tipos de proyectos** y después haga clic en el nodo **Extensibilidad**. Seleccione **Complemento de Visual Studio**.  
  
3.  Cree un nuevo proyecto de complemento con el nombre `Addin`.  
  
     En el Asistente para complementos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], haga clic en **Siguiente**.  
  
4.  En la página **Seleccione un lenguaje de programación**, elija **Crear un complemento utilizando Visual C\#** o **Crear un complemento utilizando Visual Basic**.  
  
5.  En la página **Seleccione una aplicación host**, seleccione **Microsoft Visual Studio \<version\>**.  
  
6.  En la página **Especifique un nombre y una descripción**, escriba `MyAddin` en el cuadro **Nombre** cuadro y `MyAddin Walkthrough` en el cuadro **Descripción**.  
  
7.  En la página **Elija las opciones del complemento**, seleccione la opción para un elemento del menú Herramientas en **¿Desea crear la interfaz de usuario de barra de comandos para el complemento?**. Desactive todas las demás casillas.  
  
8.  Acepte todos los valores predeterminados.  
  
9. Compile la solución y compruebe que se compila sin errores.  
  
## Obtener un servicio de un complemento  
 Los pasos siguientes le indican cómo adquirir un servicio del complemento.  
  
#### Para obtener un servicio  
  
1.  Abra el archivo Connect.cs o Connect.vb y agregue estas líneas a las instrucciones `using` \(C\#\) o `Imports` \(Visual Basic\):  
  
     [!code-cs[VSSDKAddin#1](../misc/codesnippet/CSharp/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_1.cs)]
     [!code-vb[VSSDKAddin#1](../misc/codesnippet/VisualBasic/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_1.vb)]  
  
2.  Haga clic con el botón derecho en el nodo del proyecto en **Explorador de soluciones** y agregue estas referencias de .NET:  
  
    ```  
    Microsoft.VisualStudio.OLE.Interop Microsoft.VisualStudio.Shell.Interop  
    ```  
  
3.  Agregue estas líneas de código a la cláusula `if(commandName == "Addin.Connect.Addin")` o `If commandName = "Addin.Connect.Addin" Then` del método `Exec`:  
  
     [!code-cs[VSSDKAddin#2](../misc/codesnippet/CSharp/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_2.cs)]
     [!code-vb[VSSDKAddin#2](../misc/codesnippet/VisualBasic/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_2.vb)]  
  
     Este código convierte el objeto de aplicación actual \(de tipo `DTE2`\) en `IOleServiceProvider` y luego llama a `QueryService` para obtener el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>. Este servicio ofrece una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>. El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> muestra un cuadro de mensaje cuando se ejecuta el complemento.  
  
4.  Presione F5 para compilar e iniciar el proyecto de complemento en modo de depuración.  
  
     Esto inicia otra instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
5.  En la nueva instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en el menú **Herramientas**, haga clic en **Complemento**. El cuadro de mensaje muestra lo siguiente:  
  
    ```  
    MyAddin Inside Addin.Connect  
    ```  
  
## Vea también  
 [Cómo: Desactivar y quitar un complemento](../Topic/How%20to:%20Deactivate%20and%20Remove%20an%20Add-In.md)