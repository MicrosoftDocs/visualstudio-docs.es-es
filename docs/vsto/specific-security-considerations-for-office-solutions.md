---
title: "Consideraciones de seguridad espec&#237;ficas para soluciones de Office"
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
helpviewer_keywords: 
  - "solución de problemas en el desarrollo de Office en Visual Studio, seguridad"
  - "código de confianza [desarrollo de Office en Visual Studio]"
  - "código bloqueado [desarrollo de Office en Visual Studio]"
  - "Outlook [desarrollo de Office en Visual Studio], protección del modelo de objeto"
  - "código malintencionado [desarrollo de Office en Visual Studio]"
  - "protección del modelo de objeto de Outlook [desarrollo de Office en Visual Studio]"
  - "seguridad [desarrollo de Office en Visual Studio], solución de problemas"
ms.assetid: 6a8b3e12-26c6-4ee2-a37e-d5bc8df9c5d1
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Consideraciones de seguridad espec&#237;ficas para soluciones de Office
  Las características de seguridad proporcionadas por Microsoft .NET Framework y Microsoft Office pueden ayudarle a proteger sus soluciones de Office contra diversas amenazas de seguridad. En este tema le daremos detalles acerca de esas amenazas y le proporcionaremos varias recomendaciones para que pueda protegerse contra ellas. Asimismo, este artículo también incluye información acerca de cómo influye la configuración de seguridad de Microsoft Office en las soluciones de Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## El código de confianza se manipula para que forme parte de un documento nuevo malintencionado  
 Un atacante podría usar un código de confianza diseñado para un fin determinado \(como por ejemplo, descargar información personal para una solicitud de empleo\), y volver a usarlo en otro documento, como una hoja de cálculo. El código no tiene modo de detectar que no se está ejecutando en el documento original, así que si lo abre otro usuario pueden surgir otras amenazas, como que se revele información personal o que el código se ejecute con más privilegios de lo establecido anteriormente. Otro modo extremadamente simple de hacer que la hoja de cálculo se comporte de forma anómala, es que el atacante modifique los datos de la misma antes de enviarla a la víctima. Al cambiar los valores, las fórmulas o las características de presentación de una hoja de cálculo vinculada a un código, el usuario malintencionado tiene la posibilidad de atacar a otro usuario enviándole un archivo modificado. De la misma manera, es posible hacer que los usuarios tengan acceso a información que no deberían conocer si se modifican los valores en la hoja de cálculo.  
  
 Puesto que la ubicación del ensamblado y la ubicación del documento deben tener suficientes elementos para poder ejecutarse, no es fácil llevar a cabo este ataque. Por ejemplo, los documentos que se envían como datos adjuntos de correos electrónicos o los documentos que se encuentran en servidores de intranet que no son de confianza, no tienen suficientes permisos para ejecutarse.  
  
 Para que este ataque sea posible, el propio código debe escribirse de forma que pueda tomar decisiones basadas en datos que potencialmente no sean de confianza. Un ejemplo, es crear una hoja de cálculo con una celda oculta que contenga el nombre de un servidor de base de datos. De ese modo, el usuario envía la hoja de cálculo a una página ASPX que intentará conectarse a ese servidor mediante una autenticación de SQL y una contraseña de SA \(administrador de sistema\) codificada de forma rígida. El atacante puede reemplazar el contenido de la celda oculta con un nombre de equipo diferente y obtener la contraseña de SA. Para evitar este problema, jamás codifique de forma rígida las contraseñas y, antes de acceder al servidor, compruebe en todo momento el identificador del servidor mediante una lista interna de servidores que sepa que son de confianza.  
  
### Recomendaciones  
  
-   Valide siempre las entradas y los datos, tanto si proceden del usuario, del documento, de una base de datos, de un servicio web o de cualquier otro origen.  
  
-   Tenga cuidado con ciertos tipos de funcionalidades, como obtener datos confidenciales en nombre del usuario y escribirlos en una hoja de cálculo no protegida.  
  
-   Dependiendo del tipo de aplicación que use, le será de utilidad comprobar que el documento original se está ejecutando antes de ejecutar cualquier código. Por ejemplo, compruebe que el documento que se está ejecutando está almacenado en una ubicación conocida y segura.  
  
-   Además, es una buena idea permitir que se muestre una advertencia cuando el documento se abre, si la aplicación realiza acciones con privilegios. Por ejemplo, puede crear una pantalla de presentación o un cuadro de diálogo de inicio que indique que la aplicación obtendrá acceso a información personal del usuario y hacer que el usuario elija si desea continuar o cancelar. Si el usuario final recibe una advertencia de este tipo de un documento aparentemente inocente, podrá salir de la aplicación antes de poner ninguno de sus datos en peligro.  
  
## El código está bloqueado por la protección del modelo de objetos de Outlook  
 Microsoft Office puede restringir el uso de ciertas propiedades, métodos y objetos en el modelo de objetos. Si decide restringir el acceso a esos objetos, Outlook le ayudará a evitar que tanto virus como gusanos que se propagan por medio del correo electrónico, usen el modelo de objetos para propósitos malintencionados. Esta característica de seguridad se conoce como Protección del modelo de objetos de Outlook. Si un complemento VSTO intenta usar un método o propiedad restringidos mientras esté habilitada la protección del modelo de objetos, Outlook mostrará una advertencia de seguridad que permitirá al usuario detener la operación o permitir el acceso a esa propiedad o método durante un período limitado de tiempo. Si el usuario detiene la operación, los complementos VSTO de Outlook creados mediante soluciones de Office en Visual Studio, crearán un <xref:System.Runtime.InteropServices.COMException>.  
  
 La protección del modelo de objetos puede afectar a los complementos VSTO de maneras diferentes, dependiendo de si se utiliza Outlook con Microsoft Exchange Server:  
  
-   Si no se utiliza Outlook con Exchange, un administrador puede habilitar o deshabilitar la protección del modelo de objetos para todos los complementos VSTO en el equipo.  
  
-   Si Outlook se usa con Exchange, el administrador puede habilitar o deshabilitar la protección del modelo de objetos de todos los complementos VSTO del equipo o puede permitir que ciertos complementos VSTO se ejecuten sin que se aplique la protección del modelo de objetos. Asimismo, los administradores también pueden modificar el comportamiento de la protección del modelo de objetos en determinadas áreas de ese modelo. Por ejemplo, los administradores pueden permitir mediante la programación que los complementos VSTO envíen correos electrónicos de forma automática, incluso si está habilitada la protección del modelo de objetos.  
  
 A partir de Outlook 2007, el comportamiento de la protección del modelo de objetos se ha cambiado para mejorar la experiencia del desarrollador y del usuario, a la vez que se mantiene la seguridad de Outlook. Para más información, consulte [Cambios en el código de seguridad en Outlook 2007](http://go.microsoft.com/fwlink/?LinkId=73429).  
  
### Minimizar las advertencias de protección del modelo de objetos  
 Para evitar las advertencias de seguridad cuando use propiedades y métodos restringidos, asegúrese de que el complemento VSTO obtenga objetos de Outlook desde el campo `Application` de la clase `ThisAddIn` en su proyecto. Para obtener más información sobre este campo, consulte [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
 La protección del modelo de objetos solo permitirá aquellos objetos de Outlook obtenidos de este objeto . En cambio, aquellos objetos que se obtengan de un nuevo objeto Microsoft.Office.Interop.Outlook.Application, no serán de confianza y los métodos y propiedades restringidos generarán varias advertencias de seguridad si la protección del modelo de objetos está habilitada.  
  
 En el siguiente ejemplo de código se muestra una advertencia de seguridad si está habilitada la protección del modelo de objetos. La propiedad To de la clase Microsoft.Office.Interop.Outlook.MailItem está restringida por la protección del modelo de objetos. El objeto Microsoft.Office.Interop.Outlook.MailItem no es de confianza ya que el código lo obtiene desde un Microsoft.Office.Interop.Outlook.Application que se creó mediante el operador **new**, en lugar de obtenerlo desde el campo `Application`.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreOutlookSecurity/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreOutlookSecurity/VB/ThisAddIn.vb#1)]  
  
 En el ejemplo de código siguiente se muestra cómo usar la propiedad restringida To de un objeto Microsoft.Office.Interop.Outlook.MailItem que es de confianza para la protección del modelo de objetos. El código usa el campo de confianza `Application` para obtener Microsoft.Office.Interop.Outlook.MailItem.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreOutlookSecurity/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreOutlookSecurity/VB/ThisAddIn.vb#2)]  
  
> [!NOTE]  
>  Si Outlook se utiliza con Exchange, obtener todos los objetos de Outlook desde `ThisAddIn.Application` no garantiza que el complemento VSTO pueda obtener acceso a todo el modelo de objetos de Outlook. Por ejemplo, si un administrador de Exchange configura Outlook para que deniegue automáticamente todos los intentos de obtener acceso a la información de las direcciones mediante el modelo de objetos de Outlook, Outlook no permitirá que el código del ejemplo anterior obtenga acceso a la propiedad To, aunque el código del ejemplo use el campo de confianza `ThisAddIn.Application`.  
  
### Especificar qué complementos son de confianza al usar Exchange  
 Cuando Outlook se usa con Exchange, los administradores pueden especificar que determinados complementos VSTO se ejecuten sin necesidad de acudir a la protección del modelo de objetos. Los complementos VSTO de Outlook creados mediante el uso de soluciones de Office en Visual Studio, no son de confianza por si mismos; solo se convierten en elementos de confianza si van en grupo.  
  
 Outlook confía en complementos VSTO basados en un código hash del archivo DLL de punto de entrada del mismo complemento VSTO. Todos los complementos VSTO de Outlook que tienen como destino [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usan el mismo archivo DLL de punto de entrada \(VSTOLoader.dll\). Esto significa que si un administrador confía en cualquier complemento VSTO destinado a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para que se pueda ejecutar en ausencia de la protección del modelo de objetos, todos los demás complementos VSTO destinados a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] también serán de confianza. Para obtener más información sobre cómo confiar en determinados complementos VSTO de modo que se puedan ejecutar en ausencia de la protección del modelo de objetos, consulte [Especificación del método usado por Outlook para administrar las características de prevención de virus](http://go.microsoft.com/fwlink/?LinkId=128773).  
  
## Los cambios de permiso no surten efecto inmediatamente  
 Si el administrador ajusta los permisos de un documento o de un ensamblado, los usuarios deben salir y reiniciar todas las aplicaciones de Office para que los cambios surtan efecto.  
  
 Otras aplicaciones que hospedan aplicaciones de Microsoft Office también pueden impedir que se exijan nuevos permisos. Los usuarios deben salir de todas las aplicaciones que usen Office, autónomas o no, cuando se modifican las directivas de seguridad.  
  
## La configuración del centro de confianza de Microsoft Office System no afecta a las personalizaciones de complementos o de nivel de documento  
 Los usuarios pueden evitar que los complementos VSTO se carguen si activan una opción en el **Centro de confianza**. Sin embargo, los complementos VSTO y las personalizaciones de nivel de documento creados con las soluciones de Office en Visual Studio no se ven afectados por esta configuración.  
  
 Si el usuario impide que se carguen los complementos VSTO mediante el **Centro de confianza**, no se cargarán los siguientes tipos de complementos:  
  
-   Complementos COM VSTO administrados y no administrados.  
  
-   Documentos inteligentes administrados y no administrados.  
  
-   Complementos VSTO de automatización administrados y no administrados.  
  
-   Componentes de datos en tiempo real administrados y no administrados.  
  
 Los procedimientos siguientes describen el modo en que los usuarios pueden usar el **Centro de confianza** para impedir que los complementos VSTO se carguen en Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y en Microsoft Office 2010. Estos procedimientos no afectan a los complementos VSTO o a las personalizaciones creadas mediante el uso de herramientas de desarrollo de Office en Visual Studio.  
  
#### Deshabilitar los complementos VSTO en las aplicaciones de Microsoft Office 2010 y en Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]  
  
1.  Haga clic en la pestaña **Archivo**.  
  
2.  Haga clic en el botón **Opciones** de *ApplicationName*.  
  
3.  En el panel de categorías, haga clic en **Centro de confianza**.  
  
4.  En el panel de detalles, haga clic en **Configuración del Centro de confianza**.  
  
5.  En el panel de categorías, haga clic en **Complementos**.  
  
6.  En el panel de detalles, seleccione **Solicitar que los complementos de la aplicación estén suscritos por un editor de confianza** o **Deshabilitar todos los complementos de la aplicación**.  
  
## Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)  
  
  