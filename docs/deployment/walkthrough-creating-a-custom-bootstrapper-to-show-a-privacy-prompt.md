---
title: 'Tutorial: Crear un arranque personalizado con un aviso de privacidad | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 73694df5b6e9e5d4c8b4ad40f16cf60998e9fc82
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Tutorial: Crear a un arranque personalizado con un aviso de privacidad
Puede configurar aplicaciones ClickOnce que se actualizan automáticamente cuando se convierten en ensamblados con versiones más recientes de los archivos y las versiones de ensamblado disponibles. Para asegurarse de que los clientes de consentimiento a este comportamiento, puede mostrar un aviso de privacidad a ellos. A continuación, puede elegir si se debe conceder permiso a la aplicación para actualizar automáticamente. Si la aplicación no tiene permiso para actualizar automáticamente, no se instala.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Visual Studio 2010.  
  
## <a name="create-an-update-consent-dialog-box"></a>Crear un cuadro de diálogo de consentimiento de actualización  
 Para mostrar un aviso de privacidad, cree una aplicación que pida al lector que da su consentimiento a las actualizaciones automáticas de la aplicación.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Para crear un cuadro de diálogo de consentimiento  
  
1.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, haga clic en **Windows**y, a continuación, haga clic en **WindowsFormsApplication**.  
  
3.  Para el **nombre**, tipo **ConsentDialog**y, a continuación, haga clic en **Aceptar**.  
  
4.  En el diseñador, haga clic en el formulario.  
  
5.  En el **propiedades** ventana, cambiar la **texto** propiedad **cuadro de diálogo de consentimiento de actualización**.  
  
6.  En el **cuadro de herramientas**, expanda **todos los formularios Windows Forms**y arrastre un **etiqueta** control al formulario.  
  
7.  En el diseñador, haga clic en el control de etiqueta.  
  
8.  En el **propiedades** ventana, cambiar la **texto** propiedad bajo **apariencia** al siguiente:  
  
     La aplicación que está a punto de instalar comprueba las actualizaciones más recientes en la Web. Al hacer clic en "Acepto", autoriza a la aplicación para buscar e instalar actualizaciones automáticamente desde Internet.  
  
9. En el **cuadro de herramientas**, arrastre un **casilla** control a la mitad del formulario.  
  
10. En el **propiedades** ventana, cambiar la **texto** propiedad bajo **diseño** a **acepto**.  
  
11. En el **cuadro de herramientas**, arrastre un **botón** control a la parte inferior izquierda del formulario.  
  
12. En el **propiedades** ventana, cambiar la **texto** propiedad bajo **diseño** a **continuar**.  
  
13. En el **propiedades** ventana, cambiar la **(nombre)** propiedad bajo **diseño** a **por ProceedButton**.  
  
14. En el **cuadro de herramientas**, arrastre un **botón** control a la parte inferior derecha del formulario.  
  
15. En el **propiedades** ventana, cambiar la **texto** propiedad bajo **diseño** a **cancelar**.  
  
16. En el **propiedades** ventana, cambiar la **(nombre)** propiedad bajo **diseño** a **CancelButton**.  
  
17. En el diseñador, haga doble clic en el **acepto** casilla de verificación para generar el controlador de eventos CheckedChanged.  
  
18. En el archivo de código Form1, agregue el código siguiente para el controlador de eventos CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Actualizar el constructor de clase para deshabilitar la **continuar** botón de forma predeterminada.  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. En el archivo de código Form1, agregue el siguiente código para una variable booleana para realizar un seguimiento si el usuario final ha dado su consentimiento para las actualizaciones en línea.  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. En el diseñador, haga doble clic en el **continuar** botón para generar el controlador de eventos Click.  
  
22. En el archivo de código Form1, agregue el código siguiente al controlador de eventos Click para el **continuar** botón.  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. En el diseñador, haga doble clic en el **cancelar** botón para generar el controlador de eventos Click.  
  
24. En el archivo de código Form1, agregue el código siguiente para el controlador de eventos Click para el **cancelar** botón.  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Actualizar la aplicación para devolver un error si el usuario final no da su consentimiento a las actualizaciones en línea.  
  
     Para desarrolladores de Visual Basic:  
  
    1.  En **el Explorador de soluciones**, haga clic en **ConsentDialog**.  
  
    2.  En el **proyecto** menú, haga clic en **Agregar módulo**y, a continuación, haga clic en **agregar**.  
  
    3.  En el archivo de código Module1.vb, agregue el código siguiente.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  En el **proyecto** menú, haga clic en **ConsentDialog propiedades**y, a continuación, haga clic en el **aplicación** ficha.  
  
    5.  Desactive la opción **marco de aplicación de habilitar**.  
  
    6.  En el **objeto de inicio** menú desplegable, seleccione **Module1**.  
  
        > [!NOTE]
        >  Al deshabilitar el marco de aplicación, deshabilitan características como estilos visuales de Windows XP, los eventos de aplicación, pantalla de presentación, aplicación de instancia única y mucho más. Para obtener más información, consulte [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Visual C# sólo para programadores:  
  
     Abra el archivo de código Program.cs y agregue el código siguiente.  
  
     [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. En el **generar** menú, haga clic en **compilar solución**.  
  
## <a name="create-the-custom-bootstrapper-package"></a>Crear el paquete de arranque personalizado  
 Para mostrar el aviso de privacidad para los usuarios finales, puede crear un paquete de arranque personalizado para la aplicación del cuadro de diálogo de consentimiento de actualización e incluir como un requisito previo en todas las aplicaciones de ClickOnce.  
  
 Este procedimiento muestra cómo crear un paquete de arranque personalizado mediante la creación de los siguientes documentos:  
  
-   Un product.xml manifiesto de archivo para describir el contenido del arranque.  
  
-   Un archivo de manifiesto package.xml para enumerar los aspectos específicos de la localización del paquete, como las cadenas y los términos de licencia de software.  
  
-   Un documento para los términos de licencia de software.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Paso 1: Crear el directorio de arranque  
  
1.  Cree un directorio denominado **UpdateConsentDialog** en el %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    >  Puede necesitar privilegios administrativos para crear esta carpeta.  
  
2.  En el directorio UpdateConsentDialog, cree un subdirectorio denominado es.  
  
    > [!NOTE]
    >  Crear un nuevo directorio para cada configuración regional. Por ejemplo, puede agregar subdirectorios para las configuraciones regionales fr y de. Estos directorios contendría las cadenas de francés y alemán y paquetes de idioma, si es necesario.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Paso 2: Crear el archivo de manifiesto product.xml  
  
1.  Cree un archivo de texto denominado `product.xml`.  
  
2.  En el archivo product.xml, agregue el siguiente código XML. Asegúrese de que no se sobrescriba el código XML existente.  
  
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
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Paso 3: Crear el manifiesto package.xml de archivos y el software de términos de licencia  
  
1.  Cree un archivo de texto denominado `package.xml`.  
  
2.  En el archivo package.xml, agregue el siguiente código XML para definir la configuración regional e incluir los términos de licencia de software. Asegúrese de que no se sobrescriba el código XML existente.  
  
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
  
3.  Guarde el archivo en el subdirectorio en el directorio de arranque UpdateConsentDialog.  
  
4.  Cree un documento denominado eula.rtf para los términos de licencia de software.  
  
    > [!NOTE]
    >  Los términos de licencia de software deben incluir información sobre las licencias, garantías, responsabilidades y la legislación local. Estos archivos debe ser específica de la configuración regional, así que asegúrese de que el archivo se guarda en un formato compatible con los caracteres UNICODE o MBCS. Consulte a su departamento legal sobre el contenido de los términos de licencia de software.  
  
5.  Guarde el documento en el subdirectorio en el directorio de arranque UpdateConsentDialog.  
  
6.  Si es necesario, cree un nuevo archivo de manifiesto package.xml y un nuevo documento eula.rtf para los términos de licencia de software para cada configuración regional. Por ejemplo, si ha creado subdirectorios para las configuraciones regionales fr y de, crear archivos de manifiesto package.xml independiente y los términos de licencia de software y guardarlos en los subdirectorios fr y de.  
  
## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Establecer la aplicación de consentimiento de actualización como un requisito previo  
 En Visual Studio, puede establecer la aplicación de aceptación de actualizaciones como requisito previo.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Para establecer la aplicación de aceptación de actualizaciones como requisito previo  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre de la aplicación que desea implementar.  
  
2.  En el **proyecto** menú, haga clic en *ProjectName* **propiedades**.  
  
3.  Haga clic en el **publicar** página y, a continuación, haga clic en **requisitos previos**.  
  
4.  Seleccione **actualizar el cuadro de diálogo de consentimiento**.  
  
    > [!NOTE]
    >  Tendrá que cerrar y volver a abrir Visual Studio para ver el cuadro de diálogo de consentimiento actualización en el cuadro de diálogo de requisitos previos.  
  
5.  Haga clic en **Aceptar**.  
  
## <a name="create-and-test-the-setup-program"></a>Crear y probar el programa de instalación  
 Después de establecer la aplicación de aceptación de actualizaciones como requisito previo, puede generar el instalador y el programa previo para la aplicación.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Para crear y probar el programa de instalación, no haga clic en acepto  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre de la aplicación que desea implementar.  
  
2.  En el **proyecto** menú, haga clic en *ProjectName* **propiedades**.  
  
3.  Haga clic en el **publicar** página y, a continuación, haga clic en **publicar ahora**.  
  
4.  Si el resultado de la publicación no se abre automáticamente, navegue hasta el resultado de la publicación.  
  
5.  Ejecute el programa Setup.exe.  
  
     El programa de instalación muestra el contrato de licencia de software de cuadro de diálogo de consentimiento de actualización.  
  
6.  Lea el contrato de licencia de software y, a continuación, haga clic en **Accept**.  
  
     La aplicación del cuadro de diálogo de consentimiento de actualización aparece y muestra el siguiente texto: la aplicación que está a punto de instalar comprueba las actualizaciones más recientes en la Web. Al hacer clic en acepto, autorizar la aplicación para buscar actualizaciones automáticamente en Internet.  
  
7.  Cierre la aplicación o haga clic en Cancelar.  
  
     La aplicación muestra un error: se produjo un error durante la instalación de componentes del sistema para *ApplicationName*. El programa de instalación no puede continuar hasta que se han instalado correctamente todos los componentes del sistema.  
  
8.  Haga clic en detalles para mostrar el siguiente mensaje de error: cuadro de diálogo de consentimiento de componente actualizar no se ha podido instalar con el siguiente mensaje de error: "no se acepta el contrato de actualización automática". No se pudieron instalar los siguientes componentes:-cuadro de diálogo de consentimiento de actualización  
  
9. Haga clic en **Cerrar**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Para crear y probar el programa de instalación, haga clic en acepto  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre de la aplicación que desea implementar.  
  
2.  En el **proyecto** menú, haga clic en *ProjectName* **propiedades**.  
  
3.  Haga clic en el **publicar** página y, a continuación, haga clic en **publicar ahora**.  
  
4.  Si el resultado de la publicación no se abre automáticamente, navegue hasta el resultado de la publicación.  
  
5.  Ejecute el programa Setup.exe.  
  
     El programa de instalación muestra el contrato de licencia de software de cuadro de diálogo de consentimiento de actualización.  
  
6.  Lea el contrato de licencia de software y, a continuación, haga clic en **Accept**.  
  
     La aplicación del cuadro de diálogo de consentimiento de actualización aparece y muestra el siguiente texto: la aplicación que está a punto de instalar comprueba las actualizaciones más recientes en la Web. Al hacer clic en acepto, autorizar la aplicación para buscar actualizaciones automáticamente en Internet.  
  
7.  Haga clic en **acepto**y, a continuación, haga clic en **continuar**.  
  
     La aplicación comienza a instalar.  
  
8.  Si aparece el cuadro de diálogo de instalación de la aplicación, haga clic en **instalar**.  
  
## <a name="see-also"></a>Vea también  
 [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)   
 [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md)   
 [Cómo: crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md)   
 [Cómo: crear un manifiesto del paquete](../deployment/how-to-create-a-package-manifest.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)