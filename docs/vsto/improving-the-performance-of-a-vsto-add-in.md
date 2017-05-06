---
title: "Mejorar el rendimiento de un complemento de VSTO"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 03ef25c2-6308-4737-a655-74bbbb472dc2
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Mejorar el rendimiento de un complemento de VSTO
  Puede ofrecer a los usuarios una mejor experiencia si optimiza los complementos de VSTO que cree para las aplicaciones de Office, de modo que se inicien, se cierren, abran elementos y realicen otras tareas rápidamente. Si el complemento de VSTO es para Outlook, también puede reducir la posibilidad de que se deshabilite debido a un bajo rendimiento. Puede aumentar el rendimiento del complemento de VSTO si implementa las estrategias siguientes:  
  
-   [Cargar complementos de VSTO a petición](#Load).  
  
-   [Publicar soluciones de Office mediante Windows Installer](#Publish).  
  
-   [Omitir la reflexión de la cinta de opciones](#Bypass).  
  
-   [Realizar operaciones que consumen muchos recursos en un subproceso de ejecución independiente](#Perform).  
  
 Para obtener más información sobre la optimización de un complemento de VSTO para Outlook, vea [Criterios de rendimiento para mantener los complementos de VSTO habilitados](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Cargar complementos de VSTO a petición  
 Puede configurar un complemento de VSTO de modo que se cargue solo en las siguientes circunstancias:  
  
-   La primera vez que el usuario inicie la aplicación después de instalar el complemento de VSTO.  
  
-   La primera vez que el usuario interactúe con el complemento de VSTO después de iniciar la aplicación en cualquier otro momento.  
  
 Por ejemplo, el complemento de VSTO podría rellenar una hoja de cálculo con datos cuando el usuario seleccionara un botón personalizado etiquetado como **Obtener mis datos**. La aplicación debe cargar el complemento de VSTO al menos una vez para que el botón **Obtener mis datos** pueda aparecer en la cinta de opciones. Sin embargo, el complemento de VSTO no se carga de nuevo cuando el usuario inicia la aplicación la siguiente vez. El complemento de VSTO solo se carga cuando el usuario elige el botón **Obtener mis datos**.  
  
#### Para configurar una solución ClickOnce para cargar complementos de VSTO a petición  
  
1.  En el **Explorador de soluciones**, elija el nodo de proyecto.  
  
2.  En la barra de menús, elija **Ver**, **Páginas de propiedades**.  
  
3.  En la pestaña **Publicar**, seleccione el botón **Opciones**.  
  
4.  En el cuadro de diálogo **Opciones de publicación**, seleccione el elemento de lista **Configuración de Office**, la opción **Cargar a petición** y, a continuación, el botón **Aceptar**.  
  
#### Para configurar una solución de Windows Installer para cargar complementos de VSTO a petición  
  
1.  En el Registro, establezca la entrada `LoadBehavior` de la clave *Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* en **0x10**.  
  
     Para obtener más información, consulta [Entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
#### Para configurar una solución para cargar complementos de VSTO a petición mientras se depura la solución  
  
1.  Cree un script que establezca la entrada `LoadBehavior` de la clave *Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* en **0x10**.  
  
     El código siguiente muestra un ejemplo de este script.  
  
    ```  
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn] "Description"="MyAddIn" "FriendlyName"="MyAddIn" "LoadBehavior"=dword:00000010 "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Cree un evento posterior a la compilación que actualice el Registro mediante el script.  
  
     El código siguiente muestra un ejemplo de una cadena de comando que se puede agregar a un evento posterior a la compilación.  
  
    ```  
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Para obtener información sobre la creación de eventos posteriores a la compilación en un proyecto de C\#, vea [Cómo: Especificar eventos de compilación &#40;C&#35;&#41;](~/ide/how-to-specify-build-events-csharp.md).  
  
     Para obtener información sobre la creación de eventos posteriores a la compilación en un proyecto de Visual Basic, vea [Cómo: Especificar eventos de compilación &#40;C&#35;&#41;](~/ide/how-to-specify-build-events-csharp.md).  
  
##  <a name="Publish"></a> Publicar soluciones de Office mediante Windows Installer  
 Si publica la solución mediante Windows Installer, el Visual Studio 2010 Tools para Office Runtime omite los pasos siguientes al cargar el complemento de VSTO.  
  
-   Validación del esquema del manifiesto.  
  
-   Comprobación automática de actualizaciones.  
  
-   Validación de las firmas digitales de los manifiestos de implementación.  
  
    > [!NOTE]  
    >  Este enfoque no es necesario si implementa el complemento de VSTO en una ubicación segura en los equipos de los usuarios.  
  
 Para obtener más información, consulta [Implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Omitir la reflexión de la cinta de opciones  
 Si compila una solución mediante [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], asegúrese de que los usuarios hayan instalado la versión más reciente del Motor en tiempo de ejecución de Visual Studio 2010 Tools para Office al implementar la solución. Las versiones anteriores de ese motor en tiempo de ejecución se reflejaban en los ensamblados de la solución para buscar las personalizaciones de la cinta de opciones. Este proceso puede hacer que el complemento de VSTO se cargue más lentamente.  
  
 Como alternativa, puede evitar que cualquier versión del Motor en tiempo de ejecución de Visual Studio 2010 Tools para Office use la reflexión para identificar las personalizaciones de la cinta de opciones. Para seguir esta estrategia, reemplace el método `CreateRibbonExtensibility` y devuelva los objetos de la cinta de opciones de forma explícita. Si el complemento de VSTO no contiene personalizaciones de la cinta de opciones, devuelva `null` dentro del método.  
  
 El ejemplo siguiente devuelve un objeto de la cinta de opciones en función del valor de un campo.  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
##  <a name="Perform"></a> Realizar operaciones que consumen muchos recursos en un subproceso de ejecución independiente  
 Considere la posibilidad de realizar las tareas que consumen muchos recursos \(por ejemplo, tareas de ejecución prolongada, conexiones de base de datos u otros tipos de llamadas de red\) en un subproceso independiente. Para obtener más información, consulta [Compatibilidad del subprocesamiento en Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Todo el código que llame al modelo de objetos de Office debe ejecutarse en el subproceso principal.  
  
## Vea también  
 [Carga de complementos de VSTO a petición](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Retraso de la carga del CLR en los complementos de Office](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [Rendimiento de VSTO: retraso de la carga y usuario \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [Mejoras de rendimiento próximamente en un Service Pack \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [Rendimiento de VSTO: reflexión de la cinta de opciones \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  