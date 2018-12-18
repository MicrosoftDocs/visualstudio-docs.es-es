---
title: 'Tutorial: Crear un arranque personalizado con un aviso de privacidad | Microsoft Docs'
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
ms.openlocfilehash: 18ac2ad1125067109b0ca02d552e997f2c30482f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873791"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Tutorial: Crear un programa previo personalizado con un mensaje de privacidad
Puede configurar las aplicaciones ClickOnce se actualizan automáticamente cuando estén disponibles los ensamblados con versiones más recientes de los archivos y las versiones de ensamblado. Para asegurarse de que los clientes dar su consentimiento a este comportamiento, puede mostrar un aviso de privacidad a ellos. A continuación, puede elegir si se debe conceder permiso a la aplicación se actualice automáticamente. Si la aplicación no tiene permiso para actualizar automáticamente, no se instala.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Visual Studio 2010.  
  
## <a name="create-an-update-consent-dialog-box"></a>Crear un cuadro de diálogo de consentimiento de actualización  
 Para mostrar un aviso de privacidad, cree una aplicación que solicita el lector dé su consentimiento a las actualizaciones automáticas para la aplicación.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Para crear un cuadro de diálogo de consentimiento  
  
1. En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
2. En el **nuevo proyecto** cuadro de diálogo, haga clic en **Windows**y, a continuación, haga clic en **WindowsFormsApplication**.  
  
3. Para el **nombre**, tipo **ConsentDialog**y, a continuación, haga clic en **Aceptar**.  
  
4. En el diseñador, haga clic en el formulario.  
  
5. En el **propiedades** ventana, cambie el **texto** propiedad **cuadro de diálogo de consentimiento para actualizaciones**.  
  
6. En el **cuadro de herramientas**, expanda **todos los formularios de Windows**y arrastre un **etiqueta** control al formulario.  
  
7. En el diseñador, haga clic en el control de etiqueta.  
  
8. En el **propiedades** ventana, cambie el **texto** propiedad bajo **apariencia** al siguiente:  
  
    Comprueba la aplicación que va a instalar las actualizaciones más recientes en la Web. Al hacer clic en "Acepto", autorizar a la aplicación para buscar e instalar actualizaciones automáticamente desde Internet.  
  
9. En el **cuadro de herramientas**, arrastre un **casilla** control a la mitad del formulario.  
  
10. En el **propiedades** ventana, cambie el **texto** propiedad bajo **diseño** a **acepto**.  
  
11. En el **cuadro de herramientas**, arrastre un **botón** control a la parte inferior izquierda del formulario.  
  
12. En el **propiedades** ventana, cambie el **texto** propiedad bajo **diseño** a **continuar**.  
  
13. En el **propiedades** ventana, cambie el **(nombre)** propiedad bajo **diseño** a **por ProceedButton**.  
  
14. En el **cuadro de herramientas**, arrastre un **botón** control a la parte inferior derecha del formulario.  
  
15. En el **propiedades** ventana, cambie el **texto** propiedad bajo **diseño** a **cancelar**.  
  
16. En el **propiedades** ventana, cambie el **(nombre)** propiedad bajo **diseño** a **CancelButton**.  
  
17. En el diseñador, haga doble clic en el **acepto** checkbox que genere el controlador de eventos CheckedChanged.  
  
18. En el archivo de código Form1, agregue el código siguiente para el controlador de eventos CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Actualizar el constructor de clase para deshabilitar el **continuar** botón de forma predeterminada.  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. En el archivo de código Form1, agregue el siguiente código para una variable booleana para realizar un seguimiento si el usuario final ha dado su consentimiento para actualizaciones en línea.  
  
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
  
25. Actualizar la aplicación para devolver un error si el usuario final no dar su consentimiento para actualizaciones en línea.  
  
     Para desarrolladores de Visual Basic:  
  
    1. En **el Explorador de soluciones**, haga clic en **ConsentDialog**.  
  
    2. En el **proyecto** menú, haga clic en **Agregar módulo**y, a continuación, haga clic en **agregar**.  
  
    3. En el *Module1.vb* archivo de código, agregue el código siguiente.  
  
        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4. En el **proyecto** menú, haga clic en **ConsentDialog propiedades**y, a continuación, haga clic en el **aplicación** ficha.  
  
    5. Desactive la opción **Habilitar marco de trabajo de aplicación**.  
  
    6. En el **objeto Startup** menú desplegable, seleccione **Module1**.  
  
       > [!NOTE]
       >  Al deshabilitar el marco de aplicación, deshabilitan características como los estilos visuales de Windows XP, los eventos de aplicación, pantalla de presentación, aplicación de instancia única y. Para obtener más información, consulte [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
       Visual C# sólo para programadores:  
  
       Abra el *Program.cs* archivo de código y agregue el código siguiente.  
  
       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. En el **compilar** menú, haga clic en **BuildSolution**.  
  
## <a name="create-the-custom-bootstrapper-package"></a>Crear el paquete de programa previo personalizado  
 Para mostrar el aviso de privacidad a los usuarios finales, puede crear un paquete de arranque personalizado para la aplicación del cuadro de diálogo de consentimiento para actualizaciones e incluirlo como requisito previo en todas las aplicaciones ClickOnce.  
  
 Este procedimiento muestra cómo crear un paquete de programa previo personalizado mediante la creación de los siguientes documentos:  
  
-   Un *product.xml* archivo de manifiesto para describir el contenido del programa previo.  
  
-   Un *package.xml* archivo de manifiesto para enumerar los aspectos específicos de la localización de su paquete, como cadenas y los términos de licencia del software.  
  
-   Un documento para los términos de licencia del software.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Paso 1: Crear el directorio de arranque  
  
1.  Cree un directorio denominado **UpdateConsentDialog** en el *%PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*.  
  
    > [!NOTE]
    >  Necesita privilegios administrativos para crear esta carpeta.  
  
2.  En el *UpdateConsentDialog* directorio, cree un subdirectorio denominado *en*.  
  
    > [!NOTE]
    >  Cree un nuevo directorio para cada configuración regional. Por ejemplo, puede agregar subdirectorios para las configuraciones regionales fr y de. Estos directorios contendría las cadenas de francés y alemán y paquetes de idioma, si es necesario.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Paso 2: Crear el archivo de manifiesto product.xml  
  
1.  Cree un archivo de texto llamado *product.xml*.  
  
2.  En el *product.xml* , agregue el siguiente código XML. Asegúrese de que no se sobrescriba el código XML existente.  
  
    ```xml  
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
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Paso 3: Crear el manifiesto package.xml archivo y el software de los términos de licencia  
  
1.  Cree un archivo de texto llamado *package.xml*.  
  
2.  En el *package.xml* , agregue el siguiente código XML para definir la configuración regional e incluir los términos de licencia del software. Asegúrese de que no se sobrescriba el código XML existente.  
  
    ```xml  
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
  
4.  Crear un documento denominado *eula.rtf* para los términos de licencia del software.  
  
    > [!NOTE]
    >  Los términos de licencia de software deben incluir información sobre licencias, garantía, responsabilidades y las leyes locales. Estos archivos deben ser específicos de la configuración regional, así que asegúrese de que el archivo se guarda en un formato que admita caracteres MBCS o UNICODE. Consulte su asesoría jurídica sobre el contenido de los términos de licencia del software.  
  
5.  Guarde el documento en el subdirectorio en el *UpdateConsentDialog* directorio de arranque.  
  
6.  Si es necesario, cree un nuevo *package.xml* manifiesto archivo y un nuevo *eula.rtf* documento para los términos de licencia de software para cada configuración regional. Por ejemplo, si ha creado subdirectorios para las configuraciones regionales fr y de, crear archivos de manifiesto independiente package.xml y términos de licencia del software y guardarlos en los subdirectorios fr y de.  
  
## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Establecer la actualización de consentimiento de la aplicación como un requisito previo  
 En Visual Studio, puede establecer la aplicación de aceptación de actualizaciones como requisito previo.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Para establecer la actualización de consentimiento de la aplicación como un requisito previo  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre de la aplicación que desea implementar.  
  
2.  En el **proyecto** menú, haga clic en *ProjectName* **propiedades**.  
  
3.  Haga clic en el **publicar** página y, a continuación, haga clic en **requisitos previos**.  
  
4.  Seleccione **actualizar cuadro de diálogo de consentimiento**.  
  
    > [!NOTE]
    >  Es posible que deba cerrar y volver a abrir Visual Studio para ver el cuadro de diálogo de consentimiento Update en el cuadro de diálogo requisitos previos.  
  
5.  Haga clic en **Aceptar**.  
  
## <a name="create-and-test-the-setup-program"></a>Crear y probar el programa de instalación  
 Después de configurar la aplicación de aceptación de la actualización como un requisito previo, puede generar el instalador y el programa previo para la aplicación.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Para crear y probar el programa de instalación, no haga clic en acepto  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre de la aplicación que desea implementar.  
  
2.  En el **proyecto** menú, haga clic en *ProjectName* **propiedades**.  
  
3.  Haga clic en el **publicar** página y, a continuación, haga clic en **publicar ahora**.  
  
4.  Si el resultado de la publicación no se abre automáticamente, navegue hasta el resultado de la publicación.  
  
5.  Ejecute el *Setup.exe* programa.  
  
     El programa de instalación muestra el contrato de licencia del software de cuadro de diálogo de consentimiento de actualización.  
  
6.  Lea el contrato de licencia de software y, a continuación, haga clic en **Accept**.  
  
     La aplicación del cuadro de diálogo de consentimiento de actualización aparece y muestra el siguiente texto: comprobaciones de la aplicación que va a instalar las actualizaciones más recientes en la Web. Al hacer clic en acepto, autorizar a la aplicación para buscar actualizaciones automáticamente en Internet.  
  
7.  Cierre la aplicación o haga clic en Cancelar.  
  
     La aplicación muestra un error: se produjo un error durante la instalación de componentes del sistema para *ApplicationName*. El programa de instalación no puede continuar hasta que se hayan instalado correctamente todos los componentes del sistema.  
  
8.  Haga clic en detalles para mostrar el siguiente mensaje de error: cuadro de diálogo de consentimiento de componente actualizar no se pudo instalar el siguiente mensaje de error: "no se acepta el contrato de actualización automática". No se pudo instalar los componentes siguientes:-cuadro de diálogo de consentimiento de actualización  
  
9. Haga clic en **Cerrar**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Para crear y probar el programa de instalación, haga clic en acepto  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre de la aplicación que desea implementar.  
  
2.  En el **proyecto** menú, haga clic en *ProjectName* **propiedades**.  
  
3.  Haga clic en el **publicar** página y, a continuación, haga clic en **publicar ahora**.  
  
4.  Si el resultado de la publicación no se abre automáticamente, navegue hasta el resultado de la publicación.  
  
5.  Ejecute el *Setup.exe* programa.  
  
     El programa de instalación muestra el contrato de licencia del software de cuadro de diálogo de consentimiento de actualización.  
  
6.  Lea el contrato de licencia de software y, a continuación, haga clic en **Accept**.  
  
     La aplicación del cuadro de diálogo de consentimiento de actualización aparece y muestra el siguiente texto: comprobaciones de la aplicación que va a instalar las actualizaciones más recientes en la Web. Al hacer clic en acepto, autorizar a la aplicación para buscar actualizaciones automáticamente en Internet.  
  
7.  Haga clic en **acepto**y, a continuación, haga clic en **continuar**.  
  
     La aplicación comienza a instalar.  
  
8.  Si aparece el cuadro de diálogo de instalación de la aplicación, haga clic en **instalar**.  
  
## <a name="see-also"></a>Vea también  
 [Requisitos previos de implementación de aplicación](../deployment/application-deployment-prerequisites.md)   
 [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md)   
 [Cómo: crear un manifiesto de producto](../deployment/how-to-create-a-product-manifest.md)   
 [Cómo: crear un manifiesto del paquete](../deployment/how-to-create-a-package-manifest.md)   
 [Referencia de esquema de paquete y del producto](../deployment/product-and-package-schema-reference.md)