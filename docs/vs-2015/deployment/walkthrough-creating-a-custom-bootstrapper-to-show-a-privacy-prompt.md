---
title: 'Tutorial: crear un arranque personalizado para mostrar un aviso de privacidad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d93d9f771da9387661603f3eb71301e9d9aead7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842679"
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Tutorial: Crear un arranque personalizado para mostrar un aviso de privacidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede configurar las aplicaciones ClickOnce para que se actualicen automáticamente cuando estén disponibles los ensamblados con versiones de archivos y versiones de ensamblado más recientes. Para asegurarse de que los clientes tienen el consentimiento de este comportamiento, puede mostrarles un aviso de privacidad. A continuación, pueden elegir si se debe conceder permiso a la aplicación para que se actualice automáticamente. Si no se permite que la aplicación se actualice automáticamente, no se instala.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesitará los componentes siguientes para completar este tutorial:  
  
- Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Crear un cuadro de diálogo de consentimiento de actualización  
 Para mostrar un aviso de privacidad, cree una aplicación que pida al lector que dé su consentimiento a las actualizaciones automáticas de la aplicación.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Para crear un cuadro de diálogo de consentimiento  
  
1. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.  
  
2. En el cuadro de diálogo **nuevo proyecto** , haga clic en **ventanas**y, a continuación, haga clic en **WindowsFormsApplication**.  
  
3. En el **nombre**, escriba **ConsentDialog**y, a continuación, haga clic en **Aceptar**.  
  
4. En el diseñador, haga clic en el formulario.  
  
5. En la ventana **propiedades** , cambie la propiedad **texto** a **cuadro de diálogo Actualizar consentimiento**.  
  
6. En el **cuadro de herramientas**, expanda **todos los Windows Forms**y arrastre un control **etiqueta** al formulario.  
  
7. En el diseñador, haga clic en el control etiqueta.  
  
8. En la ventana **propiedades** , cambie la propiedad **texto** en **apariencia** a lo siguiente:  
  
    La aplicación que va a instalar comprueba las actualizaciones más recientes en la Web. Al hacer clic en "Acepto", autoriza a la aplicación a buscar e instalar actualizaciones automáticamente desde Internet.  
  
9. En el **cuadro de herramientas**, arrastre un control **CheckBox** hasta el centro del formulario.  
  
10. En la ventana **propiedades** , cambie la propiedad **texto** en **diseño** a **acepto**.  
  
11. En el **cuadro de herramientas**, arrastre un control de **botón** a la parte inferior izquierda del formulario.  
  
12. En la ventana **propiedades** , cambie la propiedad **texto** en **diseño** para **continuar**.  
  
13. En la ventana **propiedades** , cambie la propiedad **(Name)** en **diseño** a **ProceedButton**.  
  
14. En el **cuadro de herramientas**, arrastre un control de **botón** hasta la parte inferior derecha del formulario.  
  
15. En la ventana **propiedades** , cambie la propiedad **texto** en **diseño** a **Cancelar**.  
  
16. En la ventana **propiedades** , cambie la propiedad **(Name)** en **diseño** a **CancelButton**.  
  
17. En el diseñador, haga doble clic en la casilla **acepto** para generar el controlador de eventos CheckedChanged.  
  
18. En el archivo de código Form1, agregue el código siguiente para el controlador de eventos CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#1)]
     [!code-vb[ConsentDialog#1](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#1)]  
  
19. Actualice el constructor de clase para deshabilitar el botón **continuar** de forma predeterminada.  
  
     [!code-csharp[ConsentDialog#6](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#6)]
     [!code-vb[ConsentDialog#6](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#6)]  
  
20. En el archivo de código Form1, agregue el siguiente código para que una variable booleana realice el seguimiento si el usuario final ha dado su consentimiento a las actualizaciones en línea.  
  
     [!code-csharp[ConsentDialog#3](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#3)]
     [!code-vb[ConsentDialog#3](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#3)]  
  
21. En el diseñador, haga doble clic en el botón **continuar** para generar el controlador de eventos Click.  
  
22. En el archivo de código Form1, agregue el código siguiente al controlador de eventos click para el botón **continuar** .  
  
     [!code-csharp[ConsentDialog#2](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#2)]
     [!code-vb[ConsentDialog#2](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#2)]  
  
23. En el diseñador, haga doble clic en el botón **Cancelar** para generar el controlador de eventos Click.  
  
24. En el archivo de código Form1, agregue el código siguiente para el controlador de eventos click para el botón **Cancelar** .  
  
     [!code-csharp[ConsentDialog#4](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#4)]
     [!code-vb[ConsentDialog#4](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#4)]  
  
25. Actualice la aplicación para que devuelva un error si el usuario final no da su consentimiento para las actualizaciones en línea.  
  
     Solo para desarrolladores de Visual Basic:  
  
    1. En **Explorador de soluciones**, haga clic en **ConsentDialog**.  
  
    2. En el menú **proyecto** , haga clic en **Agregar módulo**y, a continuación, haga clic en **Agregar**.  
  
    3. En el archivo de código Module1. VB, agregue el código siguiente.  
  
        [!code-vb[ConsentDialog#7](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb#7)]  
  
    4. En el menú **proyecto** , haga clic en **propiedades de ConsentDialog**y, a continuación, haga clic en la pestaña **aplicación** .  
  
    5. Desactive **Habilitar marco de trabajo**de la aplicación.  
  
    6. En el menú desplegable **objeto de inicio** , seleccione **Module1**.  
  
       > [!NOTE]
       > Al deshabilitar el marco de trabajo de la aplicación, se deshabilitan características como los estilos visuales de Windows XP, los eventos de aplicación, la pantalla de presentación, la aplicación de instancia única, etc. Para obtener más información, consulte [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
       Solo para desarrolladores de Visual C#:  
  
       Abra el archivo de código Program.cs y agregue el código siguiente.  
  
       [!code-csharp[ConsentDialog#5](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs#5)]  
  
26. En el menú **compilar** , haga clic en **BuildSolution**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Crear el paquete de programa previo personalizado  
 Para mostrar el aviso de privacidad a los usuarios finales, puede crear un paquete de programa previo personalizado para la aplicación de cuadro de diálogo de consentimiento de actualización e incluirlo como requisito previo en todas las aplicaciones ClickOnce.  
  
 En este procedimiento se muestra cómo crear un paquete de programa previo personalizado mediante la creación de los siguientes documentos:  
  
- Un archivo de manifiesto de product.xml para describir el contenido del programa previo.  
  
- Un archivo de manifiesto de package.xml para enumerar los aspectos específicos de la localización del paquete, como las cadenas y los términos de licencia del software.  
  
- Documento para los términos de la licencia de software.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Paso 1: para crear el directorio de arranque  
  
1. Cree un directorio denominado **UpdateConsentDialog** en%ProgramFiles%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    > Es posible que necesite privilegios de administrador para crear esta carpeta.  
  
2. En el directorio UpdateConsentDialog, cree un subdirectorio denominado en.  
  
    > [!NOTE]
    > Cree un nuevo directorio para cada configuración regional. Por ejemplo, puede Agregar subdirectorios para las configuraciones regionales fr y de. Estos directorios contendrán las cadenas y los paquetes de idioma en francés y alemán, si es necesario.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Paso 2: para crear el archivo de manifiesto de product.xml  
  
1. Cree un archivo de texto denominado `product.xml` .  
  
2. En el archivo de product.xml, agregue el siguiente código XML. Asegúrese de que no sobrescribe el código XML existente.  
  
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
  
3. Guarde el archivo en el directorio de arranque de UpdateConsentDialog.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Paso 3: para crear el archivo de manifiesto de package.xml y los términos de licencia de software  
  
1. Cree un archivo de texto denominado `package.xml` .  
  
2. En el archivo de package.xml, agregue el siguiente código XML para definir la configuración regional e incluya los términos de la licencia de software. Asegúrese de que no sobrescribe el código XML existente.  
  
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
  
3. Guarde el archivo en el subdirectorio en el directorio de arranque de UpdateConsentDialog.  
  
4. Cree un documento denominado eula. rtf para los términos de la licencia de software.  
  
    > [!NOTE]
    > Los términos de la licencia de software deben incluir información sobre licencias, garantías, responsabilidades y leyes locales. Estos archivos deben ser específicos de la configuración regional, por lo que debe asegurarse de que el archivo se guarda en un formato que admita caracteres MBCS o Unicode. Consulte al departamento legal el contenido de los términos de licencia del software.  
  
5. Guarde el documento en el subdirectorio en el directorio de arranque de UpdateConsentDialog.  
  
6. Si es necesario, cree un nuevo archivo de manifiesto de package.xml y un nuevo documento EULA. rtf para los términos de licencia de software de cada configuración regional. Por ejemplo, si creó subdirectorios para las configuraciones regionales fr y de, cree archivos de manifiesto de package.xml independientes y términos de licencia de software y guárdelos en los subdirectorios fr y de.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Configuración de la aplicación de consentimiento de actualización como requisito previo  
 En Visual Studio, puede establecer la aplicación de consentimiento de actualización como requisito previo.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Para establecer la aplicación de consentimiento de actualización como requisito previo  
  
1. En **Explorador de soluciones**, haga clic en el nombre de la aplicación que desea implementar.  
  
2. En el menú **proyecto** , haga clic en **propiedades**de *projectname* .  
  
3. Haga clic en la página **publicar** y, a continuación, haga clic en **requisitos previos**.  
  
4. Seleccione el **cuadro de diálogo Actualizar consentimiento**.  
  
    > [!NOTE]
    > Es posible que tenga que cerrar y volver a abrir Visual Studio para ver el cuadro de diálogo de consentimiento de la actualización en el cuadro de diálogo requisitos previos.  
  
5. Haga clic en **Aceptar**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Crear y probar el programa de instalación  
 Después de establecer la aplicación de consentimiento de actualización como requisito previo, puede generar el instalador y el programa previo para la aplicación.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Para crear y probar el programa de instalación sin hacer clic en Acepto  
  
1. En **Explorador de soluciones**, haga clic en el nombre de la aplicación que desea implementar.  
  
2. En el menú **proyecto** , haga clic en **propiedades**de *projectname* .  
  
3. Haga clic en la página **publicar** y, a continuación, haga clic en **publicar ahora**.  
  
4. Si el resultado de la publicación no se abre automáticamente, vaya a la salida de publicación.  
  
5. Ejecute el programa Setup.exe.  
  
     El programa de instalación muestra el contrato de licencia de software del cuadro de diálogo de consentimiento de actualización.  
  
6. Lea el contrato de licencia de software y, a continuación, haga clic en **Aceptar**.  
  
     Aparece la aplicación actualizar cuadro de diálogo de consentimiento y muestra el texto siguiente: la aplicación que va a instalar comprueba las actualizaciones más recientes en la Web. Al hacer clic en Acepto, autoriza a la aplicación a buscar actualizaciones automáticamente en Internet.  
  
7. Cierre la aplicación o haga clic en Cancelar.  
  
     La aplicación muestra un error: error al instalar componentes del sistema para *applicationName*. El programa de instalación no puede continuar hasta que todos los componentes del sistema se hayan instalado correctamente.  
  
8. Haga clic en detalles para mostrar el mensaje de error siguiente: no se pudo instalar el cuadro de diálogo de consentimiento de actualización de componentes con el mensaje de error siguiente: "no se aceptó el acuerdo de actualización automática". No se pudieron instalar los siguientes componentes:-cuadro de diálogo de consentimiento de actualización  
  
9. Haga clic en **Cerrar**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Para crear y probar el programa de instalación, haga clic en Acepto  
  
1. En **Explorador de soluciones**, haga clic en el nombre de la aplicación que desea implementar.  
  
2. En el menú **proyecto** , haga clic en **propiedades**de *projectname* .  
  
3. Haga clic en la página **publicar** y, a continuación, haga clic en **publicar ahora**.  
  
4. Si el resultado de la publicación no se abre automáticamente, vaya a la salida de publicación.  
  
5. Ejecute el programa Setup.exe.  
  
     El programa de instalación muestra el contrato de licencia de software del cuadro de diálogo de consentimiento de actualización.  
  
6. Lea el contrato de licencia de software y, a continuación, haga clic en **Aceptar**.  
  
     Aparece la aplicación actualizar cuadro de diálogo de consentimiento y muestra el texto siguiente: la aplicación que va a instalar comprueba las actualizaciones más recientes en la Web. Al hacer clic en Acepto, autoriza a la aplicación a buscar actualizaciones automáticamente en Internet.  
  
7. Haga **clic en Acepto y**, a continuación, haga clic en **continuar**.  
  
     Se inicia la instalación de la aplicación.  
  
8. Si aparece el cuadro de diálogo instalación de la aplicación, haga clic en **instalar**.  
  
## <a name="see-also"></a>Consulte también  
 [Requisitos previos de la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)   
 [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md)   
 [Cómo: crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md)   
 [Cómo: crear un manifiesto de paquete](../deployment/how-to-create-a-package-manifest.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)
