---
title: "Tutorial: Crear un arranque personalizado para mostrar un aviso de privacidad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, requisitos previos"
  - "dependencias [.NET Framework], paquete de arranque personalizado"
  - "implementar aplicaciones [Visual Studio], requisitos previos personalizados"
  - "requisitos previos [.NET Framework], paquete de arranque personalizado"
  - "implementación en Windows Installer, requisitos previos"
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# Tutorial: Crear un arranque personalizado para mostrar un aviso de privacidad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede configurar las aplicaciones ClickOnce de modo que se actualicen automáticamente cuando estén disponibles versiones más recientes de los archivos y los ensamblados.  Para asegurarse de que los clientes aceptan este comportamiento, puede mostrarles un mensaje de privacidad.  De este modo, pueden elegir si desean conceder permiso a la aplicación para que se actualice automáticamente.  Si no se permite que la aplicación se actualice automáticamente, no se instala.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Visual Studio 2010.  
  
## Crear un cuadro de diálogo de aceptación de actualizaciones  
 Para mostrar un mensaje de privacidad, cree una aplicación que pida al lector que acepte las actualizaciones automática de la aplicación.  
  
#### Para crear un cuadro de diálogo de aceptación  
  
1.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, haga clic en **Windows** y haga clic en **Aplicación de Windows Forms**.  
  
3.  En el **Nombre**, escriba ConsentDialog y, a continuación, haga clic en **Aceptar**.  
  
4.  En el diseñador, haga clic en el formulario.  
  
5.  En la ventana **Propiedades**, cambie la propiedad **Text** a Cuadro de diálogo de aceptación de actualizaciones.  
  
6.  En el **Cuadro de herramientas**, expanda **Todos los formularios Windows Forms** y arrastre un control **Label** hasta el formulario.  
  
7.  En el diseñador, haga clic en el control de etiqueta.  
  
8.  En la ventana **Propiedades**, cambie la propiedad **Text** que aparece en **Apariencia** por el siguiente código.  
  
     La aplicación que está a punto de instalar comprueba las últimas actualizaciones en la Web.  Al hacer clic en "Acepto", autoriza a la aplicación que compruebe las actualizaciones y las instale automáticamente desde Internet.  
  
9. En el **Cuadro de herramientas**, arrastre un control **Checkbox** hasta el centro del formulario.  
  
10. En la ventana **Propiedades**, cambie la propiedad **Text** que aparece en **Diseño** por Acepto.  
  
11. En el **Cuadro de herramientas**, arrastre un control **Button** a la parte inferior izquierda del formulario.  
  
12. En la ventana **Propiedades**, cambie la propiedad **Text** que aparece en **Diseño** por Continuar.  
  
13. En la ventana **Propiedades**, cambie la propiedad **\(Name\)** que aparece en **Diseño** por ProceedButton.  
  
14. En el **Cuadro de herramientas**, arrastre un control **Button** a la parte inferior derecha del formulario.  
  
15. En la ventana **Propiedades**, cambie la propiedad **Text** que aparece en **Diseño** por Cancelar.  
  
16. En la ventana **Propiedades**, cambie la propiedad **\(Name\)** que aparece en **Diseño** por CancelButton.  
  
17. En el diseñador, haga doble clic en la casilla **Acepto** para generar el controlador de eventos CheckedChanged.  
  
18. En el archivo de código Form1, agregue el siguiente código para el controlador de eventos CheckedChanged.  
  
     [!code-cs[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Actualice el constructor de clase para deshabilitar el botón **Continuar** de forma predeterminada.  
  
     [!code-cs[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. En el archivo de código de Form1, agregue el siguiente código a fin de utilizar una variable Boolean para realizar el seguimiento de si el usuario final ha aceptado a las actualizaciones en línea.  
  
     [!code-cs[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. En el diseñador, haga doble clic en el botón **Continuar** para generar el controlador de eventos Click.  
  
22. En el archivo de código Form1, agregue el código siguiente al controlador de eventos Click del botón **Continuar**.  
  
     [!code-cs[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. En el diseñador, haga doble clic en el botón **Cancelar** para generar el controlador de eventos Click.  
  
24. En el archivo de código Form1, agregue el código siguiente al controlador de eventos Click del botón **Cancelar**.  
  
     [!code-cs[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Actualice la aplicación de modo que devuelva un error si el usuario final no acepta las actualizaciones en línea.  
  
     Únicamente para desarrolladores de Visual Basic:  
  
    1.  En el **Explorador de soluciones**, haga clic en **ConsentDialog**.  
  
    2.  En el menú **Proyecto**, haga clic en **Agregar módulo** y en **Agregar**.  
  
    3.  En el archivo de código Module1.vb, agregue el siguiente código.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  En el menú **Proyecto**, haga clic en **Propiedades de ConsentDialog** y, a continuación, seleccione la pestaña **Aplicación**.  
  
    5.  Desactive **Habilitar marco de trabajo de la aplicación**.  
  
    6.  En el menú desplegable **Objeto de inicio**, seleccione **Module1**.  
  
        > [!NOTE]
        >  Al deshabilitar el marco de trabajo de la aplicación, se deshabilitan características tales como los estilos visuales de Windows XP, los eventos de aplicación, la pantalla de presentación, la aplicación de instancia única, etc.  Para obtener más información, vea [Aplicación \(Página, Diseñador de proyectos\) \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Únicamente para desarrolladores de Visual C\#:  
  
     Abra el archivo de código Program.cs y agregue el código siguiente.  
  
     [!code-cs[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. En el menú **Compilar**, haga clic en **Compilar solución**.  
  
## Crear el paquete de arranque de personalizado  
 Para mostrar el mensaje de privacidad a los usuarios finales, puede crear un paquete de arranque personalizado para la aplicación Cuadro de diálogo de aceptación de actualizaciones e incluirlo como requisito previo en todas las aplicaciones ClickOnce.  
  
 En este procedimiento se muestra cómo crear un paquete de arranque personalizado mediante la creación de los siguientes documentos:  
  
-   Un archivo de manifiesto product.xml para describir el contenido del archivo de arranque.  
  
-   Un archivo de manifiesto package.xml en que se enumeren los aspectos específicos de la localización del paquete, como las cadenas y los términos de la licencia de software.  
  
-   Un documento con los términos de la licencia de software.  
  
#### Paso 1: Crear el directorio de arranque  
  
1.  Crear un directorio denominado UpdateConsentDialog en %Archivos de programa%\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
    > [!NOTE]
    >  Puede necesitar privilegios de administrador para crear esta carpeta.  
  
2.  En el directorio UpdateConsentDialog, cree un subdirectorio denominado es.  
  
    > [!NOTE]
    >  Cree un nuevo directorio para cada configuración regional.  Por ejemplo, puede agregar subdirectorios para las configuraciones regionales fr y de.  Estos directorios contendrían las cadenas y los paquetes de idioma en francés y alemán, si fuera necesario.  
  
#### Paso 2: Crear el archivo de manifiesto product.xml  
  
1.  Cree un archivo de texto denominado `product.xml`.  
  
2.  En el archivo product.xml, agregue el siguiente código XML.  Asegúrese de no sobrescribir el código XML existente.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Guarde el archivo en el directorio de arranque UpdateConsentDialog.  
  
#### Paso 3: Crear el archivo de manifiesto package.xml y los términos de la licencia de software  
  
1.  Cree un archivo de texto denominado `package.xml`.  
  
2.  En el archivo package.xml, agregue el siguiente código XML para definir la configuración regional e incluir los términos de la licencia de software.  Asegúrese de no sobrescribir el código XML existente.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  Guarde el archivo en el subdirectorio es del directorio de arranque UpdateConsentDialog.  
  
4.  Cree un documento denominado eula.rtf para los términos de la licencia de software.  
  
    > [!NOTE]
    >  Los términos de la licencia de software deben incluir información sobre la licencia que se concede, las garantías, las responsabilidades y la legislación local.  Estos archivos deben ser específicos de la configuración regional; por ello debe asegurarse de guardarlos en un formato que admita los caracteres UNICODE o MBCS.  Consulte al departamento legal sobre el contenido de los términos de la licencia de software.  
  
5.  Guarde el documento en el subdirectorio es del directorio de arranque UpdateConsentDialog.  
  
6.  Si es necesario, cree un nuevo archivo de manifiesto package.xml y un nuevo documento eula.rtf para los términos de la licencia de software de cada configuración regional.  Por ejemplo, si ha creado subdirectorios para las configuraciones regionales fr y de, cree archivos de manifiesto package.xml y términos de licencia de software independientes y guárdelos en los subdirectorios fr y de.  
  
## Establecer la aplicación de aceptación de actualizaciones como requisito previo  
 En Visual Studio, puede establecer la aplicación de aceptación de actualizaciones como requisito previo.  
  
#### Para establecer la aplicación de aceptación de actualizaciones como requisito previo  
  
1.  En el **Explorador de soluciones**, haga clic en el nombre de la aplicación que desee implementar.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades** de *nombreDeProyecto*.  
  
3.  Haga clic en la página **Publicar** y, a continuación, haga clic en **Requisitos previos**.  
  
4.  Seleccione **Cuadro de diálogo de aceptación de actualizaciones**.  
  
    > [!NOTE]
    >  Puede que tenga que cerrar Visual Studio y volver a abrirlo para ver el Cuadro de diálogo de aceptación de actualizaciones en el cuadro de diálogo Requisitos previos.  
  
5.  Haga clic en **Aceptar**.  
  
## Crear y probar el programa de instalación  
 Después de establecer la aplicación de aceptación de actualizaciones como requisito previo, puede generar el instalador y el archivo de arranque de la aplicación.  
  
#### Para crear y probar el programa de instalación sin hacer clic en Acepto  
  
1.  En el **Explorador de soluciones**, haga clic en el nombre de la aplicación que desee implementar.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades** de *nombreDeProyecto*.  
  
3.  Haga clic en la página **Publicar** y, a continuación, en **Publicar ahora**.  
  
4.  Si la salida de publicación no se abre automáticamente, navegue hasta ella.  
  
5.  Ejecute el programa Setup.exe.  
  
     El programa Setup muestra el acuerdo de licencia de software del cuadro de diálogo de aceptación de actualizaciones.  
  
6.  Lea el contrato de licencia de software y haga clic en **Acepto**.  
  
     Aparece la aplicación de aceptación de actualizaciones con el texto siguiente: La aplicación que está a punto de instalar comprueba las últimas actualizaciones en la Web.  Al hacer clic en "Acepto", autoriza a la aplicación que compruebe las actualizaciones automáticamente en Internet.  
  
7.  Cierre la aplicación o haga clic en Cancelar.  
  
     La aplicación muestra un error: Error al instalar componentes del sistema para *nombreDeLaAplicación*.  La instalación no puede continuar hasta que todos los componentes del sistema se hayan instalado correctamente.  
  
8.  Haga clic en Detalles para mostrar el siguiente mensaje de error: No se pudo instalar el componente Cuadro de diálogo de aceptación de actualizaciones y apareció el siguiente mensaje de error: "The automatic update agreement is not accepted". Error al instalar los siguientes componentes: \- Cuadro de diálogo de aceptación de actualizaciones  
  
9. Haga clic en **Cerrar**.  
  
#### Para crear y probar el programa de instalación haciendo clic en Acepto  
  
1.  En el **Explorador de soluciones**, haga clic en el nombre de la aplicación que desee implementar.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades** de *nombreDeProyecto*.  
  
3.  Haga clic en la página **Publicar** y, a continuación, en **Publicar ahora**.  
  
4.  Si la salida de publicación no se abre automáticamente, navegue hasta ella.  
  
5.  Ejecute el programa Setup.exe.  
  
     El programa Setup muestra el acuerdo de licencia de software del cuadro de diálogo de aceptación de actualizaciones.  
  
6.  Lea el contrato de licencia de software y haga clic en **Acepto**.  
  
     Aparece la aplicación de aceptación de actualizaciones con el texto siguiente: La aplicación que está a punto de instalar comprueba las últimas actualizaciones en la Web.  Al hacer clic en "Acepto", autoriza a la aplicación que compruebe las actualizaciones automáticamente en Internet.  
  
7.  Haga clic en **Acepto** y, a continuación, en **Continuar**.  
  
     La aplicación se empieza a instalar.  
  
8.  Si aparece el cuadro de diálogo de instalación de la aplicación, haga clic en **Instalar**.  
  
## Vea también  
 [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)   
 [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md)   
 [Cómo: Crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md)   
 [Cómo: Crear un manifiesto de paquete](../deployment/how-to-create-a-package-manifest.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)