---
title: 'Tutorial: Generar código mediante plantillas de texto | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
ms.assetid: 24602ade-baca-425e-a6ce-be09a2c7f7e1
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 37fe948838a5263eca2107e2e868e2dc49cdf2a7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229377"
---
# <a name="walkthrough-generating-code-by-using-text-templates"></a>Tutorial: Generar código mediante plantillas de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La generación de código permite producir código de programa que está fuertemente tipado, pero que se puede modificar con facilidad cuando el modelo de origen cambia. Compare esto con la técnica alternativa de escribir un programa totalmente genérico que acepta un archivo de configuración, que es más flexible, pero produce código que no es tan fácil de leer ni de cambiar y que no tiene un rendimiento tan bueno. En este tutorial se muestra esta ventaja.  
  
## <a name="typed-code-for-reading-xml"></a>Código escrito para leer XML  
 El espacio de nombres System.Xml proporciona herramientas completas para cargar un documento XML y navegar por él libremente en memoria. Desgraciadamente, todos los nodos tienen el mismo tipo, XmlNode. Por lo tanto, es muy fácil cometer errores de programación, como esperar el tipo equivocado de nodo secundario o los atributos equivocados.  
  
 En este proyecto de ejemplo, una plantilla lee un archivo XML de ejemplo y genera clases que corresponden a cada tipo de nodo. En el código escrito a mano, puede usar estas clases para navegar por el archivo XML. También puede ejecutar la aplicación en otros archivos que usen los mismos tipos de nodo. El propósito del archivo XML de ejemplo es proporcionar ejemplos de todos los tipos de nodo con los que quiere que trate su aplicación.  
  
> [!NOTE]
>  La aplicación [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765), que se incluye con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede generar clases fuertemente tipadas de archivos XML. La plantilla que se muestra aquí se proporciona como ejemplo.  
  
 Este es el archivo de ejemplo:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<catalog>  
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">  
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>  
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>  
  </artist>  
  <artist id ="Euan%20Garden" name="Euan Garden">  
    <song id ="GardenScottishCountry">Scottish Country Garden</song>  
  </artist>  
</catalog>  
```  
  
 En el proyecto que se construye mediante este tutorial, puede escribir código como el siguiente e IntelliSense le presentará los nombres correctos de atributo y elemento secundario mientras escribe:  
  
```  
Catalog catalog = new Catalog(xmlDocument);  
foreach (Artist artist in catalog.Artist)  
{  
  Console.WriteLine(artist.name);  
  foreach (Song song in artist.Song)  
  {  
    Console.WriteLine("   " + song.Text);  
  }  
}  
```  
  
 Compare esto con el código sin tipo que se escribiría sin la plantilla:  
  
```  
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");  
foreach (XmlNode artist in catalog.SelectNodes("artist"))  
{  
    Console.WriteLine(artist.Attributes["name"].Value);  
    foreach (XmlNode song in artist.SelectNodes("song"))  
    {  
         Console.WriteLine("   " + song.InnerText);  
     }  
}  
```  
  
 En la versión fuertemente tipada, un cambio en el esquema XML producirá cambios en las clases. El compilador resaltará las partes del código de aplicación que se deben cambiar. En la versión sin tipo que usa código XML genérico, no existe esa posibilidad.  
  
 En este proyecto, se usa un solo archivo de plantilla para generar las clases que hacen posible la versión con tipo.  
  
## <a name="setting-up-the-project"></a>Configurar el proyecto  
  
### <a name="create-or-open-a-c-project"></a>Crear o abrir un proyecto en C#  
 Puede aplicar esta técnica a cualquier proyecto de código. En este tutorial se usa un proyecto de C#, mientras que para la realización de las pruebas se usa una aplicación de consola.  
  
##### <a name="to-create-the-project"></a>Para crear el proyecto  
  
1.  En el menú **Archivo** , haga clic en **Nuevo** y, después, haga clic en **Proyecto**.  
  
2.  Haga clic en el nodo **Visual C#** y, en el panel **Plantillas** , haga clic en **Aplicación de consola**.  
  
### <a name="add-a-prototype-xml-file-to-the-project"></a>Agregar un archivo XML de prototipo al proyecto  
 El propósito de este archivo es proporcionar ejemplos de los tipos de nodo XML que quiere que lea su aplicación. Puede ser un archivo que se usará para probar la aplicación. La plantilla producirá una clase de C# para cada tipo de nodo de este archivo.  
  
 El archivo debe formar parte del proyecto para que la plantilla pueda leerlo, pero no se integrará en la aplicación compilada.  
  
##### <a name="to-add-an-xml-file"></a>Para agregar un archivo XML  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto, haga clic en **Agregar** y después en **Nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Archivo XML** en el panel **Plantillas** .  
  
3.  Agregue el contenido de ejemplo al archivo.  
  
4.  Para este tutorial, asigne al archivo el nombre `exampleXml.xml`. Establezca el contenido del archivo de modo que sea el XML que se muestra en la sección anterior.  
  
 .  
  
### <a name="add-a-test-code-file"></a>Agregar un archivo de código de prueba  
 Agregue un archivo de C# al proyecto y escriba en él un ejemplo del código que quiere poder escribir. Por ejemplo:  
  
```  
using System;  
namespace MyProject  
{  
  class CodeGeneratorTest  
  {  
    public void TestMethod()  
    {  
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");  
      foreach (Artist artist in catalog.Artist)  
      {  
        Console.WriteLine(artist.name);  
        foreach (Song song in artist.Song)  
        {  
          Console.WriteLine("   " + song.Text);  
} } } } }  
```  
  
 En esta fase, este código no se compila. A medida que escribe la plantilla, generará las clases que permiten que se compile correctamente.  
  
 Una prueba más completa podría comprobar la salida de esta función de prueba con el contenido conocido del archivo XML de ejemplo. Pero, en este tutorial, nos basta con que el método de prueba se compile.  
  
### <a name="add-a-text-template-file"></a>Agregar un archivo de plantilla de texto  
 Agregue un archivo de plantilla de texto y establezca la extensión de salida en ".cs".  
  
##### <a name="to-add-a-text-template-file-to-your-project"></a>Para agregar un archivo de plantilla de texto al proyecto  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto, haga clic en **Agregar**y después en **Nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Plantilla de texto** en el panel **Plantillas** .  
  
    > [!NOTE]
    >  Asegúrese de agregar una plantilla de texto y no una plantilla de texto preprocesada.  
  
3.  En la directiva de plantilla del archivo, cambie el atributo `hostspecific` a `true`.  
  
     Este cambio permitirá que el código de plantilla obtenga acceso a los servicios de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
4.  En la directiva de salida, cambie el atributo de extensión a ".cs" para que la plantilla genere un archivo de C#. En un proyecto de Visual Basic, lo cambiaría a ".vb".  
  
5.  Guarde el archivo. En esta fase, el archivo de plantilla de texto debe contener estas líneas:  
  
    ```  
    <#@ template debug="false" hostspecific="true" language="C#" #>  
    <#@ output extension=".cs" #>  
    ```  
  
 .  
  
 Observe que aparece un archivo .cs en el Explorador de soluciones como subsidiario del archivo de plantilla. Puede verlo haciendo clic en [+] junto al nombre del archivo de plantilla. Este archivo se genera a partir del archivo de plantilla cada vez que guarde o mueva el foco fuera del archivo de plantilla. El archivo generado se compilará como parte de su proyecto.  
  
 Para mayor comodidad mientras desarrolla el archivo de plantilla, organice las ventanas del archivo de plantilla y del archivo generado de modo que pueda verlos uno al lado del otro. Esto le permite ver inmediatamente la salida de la plantilla. También observará que, cuando la plantilla genere código de C# no válido, aparecerán errores en la ventana de mensajes de error.  
  
 Las modificaciones que realice directamente en el archivo generado se perderán cuando guarde el archivo de plantilla. Por eso, debe evitar modificar el archivo generado, o editarlo solo para realizar breves experimentos. A veces resulta útil probar un fragmento corto de código en el archivo generado donde IntelliSense esté en funcionamiento y, después, copiarlo en el archivo de plantilla.  
  
## <a name="developing-the-text-template"></a>Desarrollar la plantilla de texto  
 Siguiendo las recomendaciones para un desarrollo ágil, desarrollaremos la plantilla en pasos pequeños, eliminando algunos errores en cada incremento, hasta que el código de prueba se compile y se ejecute correctamente.  
  
### <a name="prototype-the-code-to-be-generated"></a>Crear un prototipo del código que se va a generar  
 El código de prueba requiere una clase para cada nodo del archivo. Por lo tanto, algunos de los errores de compilación desaparecerán si anexa estas líneas a la plantilla y después la guarda:  
  
```  
class Catalog {}   
class Artist {}  
class Song {}  
```  
  
 Esto le ayuda a ver lo que es necesario, pero las declaraciones se deben generar a partir de los tipos de nodo del archivo XML de ejemplo. Elimine estas líneas experimentales de la plantilla.  
  
### <a name="generate-application-code-from-the-model-xml-file"></a>Generar código de aplicación a partir del archivo XML del modelo  
 Para leer el archivo XML y generar declaraciones de clase, reemplace el contenido de la plantilla por el siguiente código de plantilla:  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml"#>  
<#@ import namespace="System.Xml" #>  
<#  
 XmlDocument doc = new XmlDocument();  
 // Replace this file path with yours:  
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
#>  
  public partial class <#= node.Name #> {}  
<#  
 }  
#>  
```  
  
 Reemplace la ruta de acceso del archivo por la ruta de acceso correcta para su proyecto.  
  
 Observe los delimitadores de bloque de código `<#...#>`. Estos delimitadores separan un fragmento del código de programa que genera el texto. Los delimitadores de bloque de expresión `<#=...#>` separan una expresión que se puede evaluar como una cadena.  
  
 Cuando escribe una plantilla que genera código fuente para la aplicación, está tratando con dos textos de programas independientes. El programa incluido dentro de los delimitadores de bloque de código se ejecuta cada vez que se guarda la plantilla o se mueve el foco a otra ventana. El texto que genera, que aparece fuera de los delimitadores, se copia en el archivo generado y pasa a formar parte del código de aplicación.  
  
 La directiva `<#@assembly#>` se comporta como una referencia, lo que hace que el ensamblado esté disponible para el código de plantilla. La lista de ensamblados que la plantilla ve es independiente de la lista de referencias en el proyecto de aplicación.  
  
 La directiva `<#@import#>` actúa como una instrucción `using` , lo que permite usar los nombres cortos de las clases del espacio de nombres importado.  
  
 Desgraciadamente, aunque esta plantilla genera código, produce una declaración de clase para cada nodo del archivo XML de ejemplo, por lo que si hay varias instancias del nodo `<song>` , aparecerán varias declaraciones de la clase song.  
  
### <a name="read-the-model-file-then-generate-the-code"></a>Leer el archivo de modelo y después generar el código  
 Muchas plantillas de texto siguen un patrón según el cual la primera parte de la plantilla lee el archivo de origen y la segunda parte genera la plantilla. Necesitamos leer todo el archivo de ejemplo para resumir los tipos de nodo que contiene y luego generar las declaraciones de clase. Hace falta otra directiva `<#@import#>` para que podemos usar `Dictionary<>:`  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml"#>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.Collections.Generic" #>  
<#  
 // Read the model file  
 XmlDocument doc = new XmlDocument();  
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");  
 Dictionary <string, string> nodeTypes =   
        new Dictionary<string, string>();  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
   nodeTypes[node.Name] = "";  
 }  
 // Generate the code  
 foreach (string nodeName in nodeTypes.Keys)  
 {  
#>  
  public partial class <#= nodeName #> {}  
<#  
 }  
#>  
```  
  
### <a name="add-an-auxiliary-method"></a>Agregar un método auxiliar  
 Un bloque de control de características de clase es un bloque en el que se pueden definir métodos auxiliares. El bloque se delimita con `<#+...#>` y debe aparecer como el último bloque del archivo.  
  
 Si prefiere que los nombres de clase empiecen con una letra mayúscula, puede reemplazar la última parte de la plantilla por el siguiente código de plantilla:  
  
```  
// Generate the code  
 foreach (string nodeName in nodeTypes.Keys)  
 {  
#>  
  public partial class <#= UpperInitial(nodeName) #> {}  
<#  
 }  
#>  
<#+  
 private string UpperInitial(string name)  
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }  
#>  
```  
  
 En esta fase, el archivo .cs generado contiene las declaraciones siguientes:  
  
```  
public partial class Catalog {}  
public partial class Artist {}  
public partial class Song {}  
```  
  
 Usando este mismo enfoque se pueden agregar más detalles, como propiedades de los nodos secundarios, atributos y texto interno.  
  
### <a name="accessing-the-visual-studio-api"></a>Obtener acceso a la API de Visual Studio  
 Si establece el atributo `hostspecific` de la directiva `<#@template#>` , la plantilla puede tener acceso a la API de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . De este modo, la plantilla puede obtener la ubicación de los archivos de proyecto para evitar el uso de una ruta de acceso a archivo absoluta en el código de plantilla.  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
...  
<#@ assembly name="EnvDTE" #>  
...  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
// Open the prototype document.  
XmlDocument doc = new XmlDocument();  
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));  
```  
  
## <a name="completing-the-text-template"></a>Completar la plantilla de texto  
 El siguiente contenido de la plantilla genera código que permite compilar y ejecutar el código de prueba.  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".cs" #>  
<#@ assembly name="System.Xml" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.Collections.Generic" #>  
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{  
<#  
 // Map node name --> child name --> child node type  
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();  
  
 // The Visual Studio host, to get the local file path.  
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
 // Open the prototype document.  
 XmlDocument doc = new XmlDocument();  
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));  
 // Inspect all the nodes in the document.  
 // The example might contain many nodes of the same type,   
 // so make a dictionary of node types and their children.  
 foreach (XmlNode node in doc.SelectNodes("//*"))  
 {  
   Dictionary<string, XmlNodeType> subs = null;  
   if (!nodeTypes.TryGetValue(node.Name, out subs))  
   {  
     subs = new Dictionary<string, XmlNodeType>();  
     nodeTypes.Add(node.Name, subs);  
   }  
   foreach (XmlNode child in node.ChildNodes)  
   {  
     subs[child.Name] = child.NodeType;  
   }   
   foreach (XmlNode child in node.Attributes)  
   {  
     subs[child.Name] = child.NodeType;  
   }  
 }  
 // Generate a class for each node type.  
 foreach (string className in nodeTypes.Keys)  
 {  
    // Capitalize the first character of the name.  
#>  
    partial class <#= UpperInitial(className) #>  
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }  
  
<#  
    // Generate a property for each child.  
    foreach (string childName in nodeTypes[className].Keys)  
    {  
      // Allow for different types of child.  
      switch (nodeTypes[className][childName])  
      {  
         // Child nodes:  
         case XmlNodeType.Element:  
#>  
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }  
<#  
         break;  
         // Child attributes:  
         case XmlNodeType.Attribute:  
#>  
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }  
<#  
         break;  
         // Plain text:  
         case XmlNodeType.Text:  
#>  
      public string Text  { get { return thisNode.InnerText; } }  
<#  
         break;  
       } // switch  
     } // foreach class child  
  // End of the generated class:  
#>  
   }   
<#  
 } // foreach class  
  
   // Add a constructor for the root class   
   // that accepts an XML filename.  
   string rootClassName = doc.SelectSingleNode("*").Name;  
#>  
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}  
<#+  
   private string UpperInitial(string name)  
   {  
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);  
   }  
#>  
```  
  
### <a name="running-the-test-program"></a>Ejecutar el programa de prueba  
 En la ventana principal de la aplicación de consola, las siguientes líneas ejecutarán el método de prueba. Pulse F5 para ejecutar el programa en modo de depuración:  
  
```  
using System;  
namespace MyProject  
{ class Program  
  { static void Main(string[] args)  
    { new CodeGeneratorTest().TestMethod();  
      // Allow user to see the output:  
      Console.ReadLine();  
} } }  
```  
  
### <a name="writing-and-updating-the-application"></a>Escribir y actualizar la aplicación  
 Ahora la aplicación se puede escribir en un estilo fuertemente tipado usando las clases generadas en lugar de código XML genérico.  
  
 Cuando el esquema XML cambie, se podrán generar fácilmente clases nuevas. El compilador le indicará al desarrollador dónde es necesario actualizar el código de aplicación.  
  
 Para volver a generar las clases cuando el archivo XML de ejemplo cambie, haga clic en **Transformar todas las plantillas** en la barra de herramientas del Explorador de soluciones.  
  
## <a name="conclusion"></a>Conclusión  
 En este tutorial se muestran varias técnicas y ventajas de la generación de código:  
  
-   La*generación de código* es la creación de parte del código fuente de la aplicación a partir de un *modelo*. El modelo contiene información en un formato adecuado para el dominio de aplicación y puede cambiar durante la vigencia de la aplicación.  
  
-   El tipado fuerte es una de las ventajas de la generación de código. Aunque el modelo representa la información en un formato más adecuado para el usuario, el código generado permite que otras partes de la aplicación traten la información con un conjunto de tipos.  
  
-   IntelliSense y el compilador ayudan a crear código que cumple el esquema del modelo, tanto al escribir código nuevo como al actualizar el esquema.  
  
-   La adición de un único archivo de plantilla poco complicado a un proyecto puede proporcionar estas ventajas.  
  
-   Es posible desarrollar y probar rápidamente y de manera incremental una plantilla de texto.  
  
 En este tutorial, el código de programa se genera realmente desde una instancia del modelo, que es un ejemplo representativo de los archivos XML que la aplicación va a procesar. Siguiendo un enfoque más formal, el esquema XML sería la entrada a la plantilla, en forma de archivo .xsd o definición de lenguaje específico de dominio. Este enfoque puede facilitar que la plantilla determine características como la multiplicidad de una relación.  
  
## <a name="troubleshooting-the-text-template"></a>Solución de problemas de la plantilla de texto  
 Si ve errores de compilación o de transformación de la plantilla en la **Lista de errores**, o si el archivo de salida no se genera correctamente, puede solucionar los problemas de la plantilla de texto con las técnicas descritas en [Generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
## <a name="see-also"></a>Vea también  
 [Generación de código en tiempo de diseño usando las plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)



