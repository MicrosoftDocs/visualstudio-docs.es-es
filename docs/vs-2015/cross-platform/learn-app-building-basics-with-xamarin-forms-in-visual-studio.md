---
title: Información sobre los conceptos básicos de la compilación de aplicaciones con Xamarin. Forms
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: bc7e46af7e29ef554b80bd9244910e0c67d373af
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299766"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Información sobre los conceptos básicos de la compilación de aplicaciones con Xamarin.Forms en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tras realizar los pasos [Setup and install](../cross-platform/setup-and-install.md) y [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md), en este tutorial se muestra cómo compilar una aplicación básica (se muestra a continuación) con Xamarin.Forms. Con Xamarin.Forms, escribirá todo el código de interfaz de usuario una vez en una biblioteca de clases portable (PCL). Después, Xamarin representará de forma automática los controles de interfaz de usuario nativos para las plataformas iOS, Android y Windows. Se recomienda este enfoque porque la opción de PCL es la más compatible al usar solo esas API de .NET que son compatibles con todas las plataformas de destino, y porque Xamarin.Forms le permite compartir código de interfaz de usuario entre plataformas.

 ![El ejemplo de aplicación meteorológica en Android, iOS y Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

 Deberá llevar a cabo estas operaciones para compilarla:

- [Configurar la solución](#solution)

- [Escribir código de servicio de datos compartidos](#dataservice)

- [Empezar a escribir código de interfaz de usuario compartido](#uicode)

- [Probar la aplicación mediante el emulador de Visual Studio para Android](#test)

- [Finalice la interfaz de usuario con una apariencia nativa en todas las plataformas](#finish)

> [!TIP]
> Puede encontrar el código fuente completo para este proyecto en el [repositorio xamarin-forms-samples en GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

## <a name="solution"></a> Configurar la solución
 En estos pasos, se crea una solución de Xamarin.Forms que contiene una PCL para código compartido y dos paquetes NuGet agregados.

1. En Visual Studio, cree una nueva solución de **Aplicación vacía (Xamarin.Forms Portable)** con el nombre **WeatherApp**. Puede encontrar esta plantilla con mayor facilidad si escribe **Xamarin.Forms** en el campo de búsqueda.

     Si no la encuentra, es posible que tenga que instalar Xamarin o habilitar la característica de Visual Studio 2015. Vea [Configuración e instalación](../cross-platform/setup-and-install.md).

     ![Creación de un nuevo proyecto &#40;portable&#41; de Xamarin. Forms aplicación en blanco](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2. Después de hacer clic en Aceptar para crear la solución, tendrá un número de proyectos individuales:

    - **WeatherApp (Portable)** : la PCL en la que escribirá código que se comparte entre plataformas, incluida la lógica de negocios común y el código de interfaz de usuario con Xamarin.Forms.

    - **WeatherApp.Droid**: el proyecto que contiene el código nativo de Android. Este se establece como el proyecto de inicio predeterminado.

    - **WeatherApp.iOS**: el proyecto que contiene el código nativo de iOS.

    - **WeatherApp.UWP**: el proyecto que contiene el código nativo de Windows 10 UWP.

    - **WeatherApp.Windows (Windows 8.1)** : el proyecto que contiene el código nativo de Windows 8.1.

    - **WeatherApp.WinPhone (Windows Phone 8.1)** : el proyecto que contiene el código nativo de Windows Phone.

    > [!NOTE]
    > Puede eliminar cualquiera de los proyectos de una plataforma que no tenga como destino. A los efectos de este tutorial, nos referiremos a los proyectos de Android, iOS y Windows Phone 8.1. Trabajar con proyectos de UWP y Windows 8.1 es muy similar a trabajar con el proyecto de Windows Phone 8.1.

     En cada proyecto nativo tiene acceso al diseñador nativo de la plataforma correspondiente y puede implementar pantallas y características específicas de la plataforma según sea necesario.

3. Actualice el paquete de NuGet Xamarin.Forms en la solución a la última versión estable como sigue. Se recomienda hacerlo siempre que cree una nueva solución de Xamarin:

    - Seleccione **Herramientas > Administrador de paquetes NuGet > Administrar paquetes NuGet para la solución**.

    - En la pestaña **Actualizaciones** , marque la actualización **Xamarin.Forms** y marque que se actualicen todos los proyectos de la solución. (Nota: deje las actualizaciones de Xamarin.Android.Support desactivadas).

    - Actualice el campo **Versión** a la versión **estable más reciente** disponible.

    - Haga clic en **Actualizar**.

         ![Actualización del paquete NuGet de Xamarin. Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

4. Agregue **Newtonsoft.Json** y el paquete NuGet al proyecto PCL, que usará para procesar la información recuperada de un servicio de datos de tiempo:

    - En el Administrador de paquetes NuGet (sigue abierto desde el paso 3), seleccione la pestaña **Examinar** y busque **Newtonsoft**.

    - Seleccione **Newtonsoft.Json**.

    - Marque el proyecto **WeatherApp** (es el único proyecto en el que debe instalar el paquete).

    - Asegúrese de que el campo **Versión** está establecido en la versión **estable más reciente** .

    - Haga clic en **Instalar**.

    - ![Buscar e instalar el paquete NuGet Newtonsoft. JSON](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

5. Repita el paso 4 para buscar e instalar el paquete **Microsoft.Net.Http** .

6. Compile la solución y compruebe que no hay ningún error de compilación.

## <a name="dataservice"></a> Escribir código de servicio de datos compartidos
 El proyecto **WeatherApp (Portable)** es en el que escribirá el código de la biblioteca de clases portable (PCL) que se comparte entre todas las plataformas. La PCL se incluye de forma automática en la compilación de paquetes de la aplicación mediante los proyectos de iOS, Android y Windows Phone.

 Para ejecutar este ejemplo, primero debe registrarse para obtener una clave de API gratuita en [http://openweathermap.org/appid](https://openweathermap.org/appid).

 En los pasos siguientes, se agrega el código a la PCL para acceder y almacenar datos de ese servicio meteorológico:

1. Haga clic con el botón derecho en el proyecto **WeatherApp** y seleccione **Agregar > Clase...** . En el cuadro de diálogo **Agregar nuevo elemento** , denomine al archivo **Weather.cs**. Esta clase se usará para almacenar los datos del servicio de datos meteorológicos.

2. Reemplace todo el contenido de **Weather.cs** por lo siguiente:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

3. Agregue otra clase al proyecto PCL denominado **DataService.cs** que usará para procesar los datos JSON del servicio de datos meteorológicos.

4. Reemplace todo el contenido de **DataService.cs** por el código siguiente:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

5. Agregue una tercera clase a la PCL denominada **Core** en la que pondrá la lógica de negocios compartida, como la lógica que forma una cadena de consulta con un código postal, llama al servicio de datos meteorológicos y rellena una instancia de la clase **Weather** .

6. Reemplace el contenido de **Core.cs** por lo siguiente:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

7. Compile el proyecto de PCL **WeatherApp** para asegurarse de que el código es correcto.

## <a name="uicode"></a> Empezar a escribir código de interfaz de usuario compartido
 Xamarin.Forms le permite implementar el código de interfaz de usuario compartido en la PCL. En estos pasos, agregará una pantalla a la PCL con un botón que actualiza su texto con datos que devuelve el código del servicio de datos meteorológicos agregado en la sección anterior:

1. Agregue una **página XAML de formularios** denominada **WeatherPage.CS** haciendo clic con el botón derecho en el proyecto **WeatherApp** y seleccionando **Agregar > nuevo elemento..** .. En el cuadro de diálogo **Agregar nuevo elemento** , busque "Forms", seleccione **Forms XAML Page**y asígnele el nombre **WeatherPage.CS**.

     Xamarin.Forms está basado en XAML, por lo que, en este paso, se crea un archivo **WeatherPage.xaml** junto con el archivo de código subyacente anidado **WeatherPage.xaml.cs**. Esto le permite generar la interfaz de usuario mediante código o XAML. Realizará ambos en este tutorial.

     ![Agregar una nueva página XAML de Xamarin. Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

2. Para agregar un botón a la pantalla WeatherPage, reemplace el contenido de WeatherPage.xaml por lo siguiente:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     Tenga en cuenta que el nombre del botón debe definirse mediante el atributo **x:Name** para que pueda hacer referencia a este botón por nombre desde el archivo de código subyacente.

3. Para agregar un controlador de eventos al evento **Clicked** del botón para actualizar el texto del botón, reemplace el contenido de **WeatherPage.xaml.cs** por el código siguiente. (No dude en cambiar "60601" por otro código postal).

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();
                this.Title = "Sample Weather App";
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;

                //Set the default binding to a default object for now
                this.BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4. Para abrir **WeatherPage** como la primera pantalla cuando se inicia la aplicación, reemplace el constructor predeterminado en **App.cs** por el código siguiente:

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5. Compile el proyecto de PCL WeatherApp para asegurarse de que el código es correcto.

## <a name="test"></a> Probar la aplicación mediante el emulador de Visual Studio para Android
 Ahora ya está listo para ejecutar la aplicación. Vamos a ejecutar solo la versión de Android por ahora para comprobar que la aplicación obtiene datos del servicio meteorológico. Más adelante, también ejecutará las versiones de Windows Phone y iOS después de agregar más elementos de interfaz de usuario. (Nota: si ejecuta Visual Studio en Windows 7, deberá seguir estos mismos pasos pero con Xamarin Player en su lugar).

1. Establezca el proyecto **WeatherApp.Droid** como el proyecto de inicio; para ello, haga clic en él con el botón derecho y seleccione **Establecer como proyecto de inicio**.

2. En la barra de herramientas de Visual Studio, verá que **WeatherApp.Droid** aparece como el proyecto de destino. Seleccione uno de los emuladores de Android para depurar y pulse **F5**. Se recomienda usar una de las opciones de **emulador de VS** que ejecutarán la aplicación en las opciones del emulador de Visual Studio para Android.

     ![Seleccionar un destino de depuración del emulador de VS](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

3. Cuando se inicie la aplicación en el emulador, haga clic en el botón **Obtener tiempo** . Debería ver el texto del botón actualizado a **Chicago, IL**, que es la propiedad *Title* de los datos recuperados del servicio meteorológico.

     ![Aplicación meteorológica antes y después de pulsar el botón](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

## <a name="finish"></a> Finalizar la interfaz de usuario con una apariencia nativa en todas las plataformas
 Xamarin.Forms representa los controles de interfaz de usuario nativos de cada plataforma, para que la aplicación tenga una apariencia nativa de forma automática. Para ver esto de forma más clara, finalizaremos la interfaz de usuario con un campo de entrada para un código postal y, después, se mostrarán los datos meteorológicos que devuelve el servicio.

1. Reemplace el contenido de **WeatherPage.xaml** por el código siguiente. Tenga en cuenta que cada elemento se denomina mediante el atributo **x:Name** tal y como se ha descrito anteriormente, para que se pueda hacer referencia al elemento desde el código. Xamarin.Forms también proporciona un número de [opciones de diseño](https://docs.microsoft.com/xamarin/xamarin-forms/user-interface/controls/layouts) (xamarin.com); en este caso, WeatherPage usa [StackLayout](https://docs.microsoft.com/dotnet/api/Xamarin.Forms.StackLayout?view=xamarin-forms) (xamarin.com).

   ```xaml
   <?xml version="1.0" encoding="utf-8" ?>
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
          x:Class="WeatherApp.WeatherPage">

     <ContentPage.Resources>
       <ResourceDictionary>
         <Style x:Key="labelStyle" TargetType="Label">
           <Setter Property="TextColor" Value="#a8a8a8" />
           <Setter Property="FontSize" Value="Small" />
         </Style>
         <Style x:Key="fieldStyle" TargetType="Label">
           <Setter Property="TextColor">
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />
           </Setter>
           <Setter Property="FontSize" Value="Medium" />
         </Style>
         <Style x:Key="fieldView" TargetType="ContentView">
           <Setter Property="Padding" Value="10,0,0,0" />
         </Style>
       </ResourceDictionary>
     </ContentPage.Resources>

     <ContentPage.Content>
       <ScrollView>
         <StackLayout>
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"
                 BackgroundColor="#545454">
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"
                   FontSize="Medium" />
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />
               <Entry x:Name="zipCodeEntry" />
             </StackLayout>
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >
                 <!-- Set iOS colors; use defaults on other platforms -->
                 <Button.TextColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.TextColor>
                 <Button.BorderColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.BorderColor>
               </Button>
             </StackLayout>
           </StackLayout>
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
             <Label Text="Location" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="tempLabel" Text="{Binding Temperature}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
           </StackLayout>
         </StackLayout>
       </ScrollView>
     </ContentPage.Content>
   </ContentPage>
   ```

    Fíjese en el uso de la etiqueta **OnPlatform** en Xamarin.Forms. **OnPlatform** selecciona un valor de propiedad que es específico de la plataforma actual en la que se ejecuta la aplicación (consulte [External XAML Syntax (Sintaxis XAML externa)](https://docs.microsoft.com/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax) (xamarin.com). Lo usamos aquí para establecer un color de texto diferente para los campos de datos: blanco en Android y Windows Phone, negro en iOS. Puede usar **OnPlatform** en cualquier propiedad y tipo de datos para realizar ajustes específicos de la plataforma en cualquier lugar en el código XAML. En el archivo de código subyacente, puede usar la [API Device.OnPlatform](https://docs.microsoft.com/xamarin/xamarin-forms/platform/device) para el mismo propósito.

2. En **WeatherPage.xaml.cs**, reemplace el controlador de eventos **GetWeatherBtn_Clicked** por el código siguiente. Este código comprueba que hay un código postal en el campo de entrada, recupera datos de ese código postal, establece el contexto de enlace de la pantalla completa para la instancia Weather resultante y, después, establece el texto del botón en "Buscar de nuevo". Tenga en cuenta que cada etiqueta de la interfaz de usuario enlaza a una propiedad de la clase Weather, así que cuando establece el contexto de enlace de la pantalla en una instancia **Weather** , esas etiquetas se actualizan de forma automática.

   ```csharp
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
   {
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))
       {
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);
           this.BindingContext = weather;
           getWeatherBtn.Text = "Search Again";
       }
   }
   ```

3. Ejecute la aplicación en las tres plataformas: Android, iOS y Windows Phone. Para ello, haga clic con el botón derecho en el proyecto adecuado, seleccione Establecer como proyecto de inicio e inicie la aplicación en un dispositivo, en el emulador o en el simulador. Escriba un código postal de Estados Unidos válido (por ejemplo, 60601) y haga clic en el botón Obtener tiempo para mostrar los datos meteorológicos de esa región, como se muestra a continuación. Por supuesto, necesitará tener Visual Studio conectado a un equipo Mac OS X en la red para el proyecto de iOS.

    ![El ejemplo de aplicación meteorológica en Android, iOS y Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

   Puede encontrar el código fuente completo de este proyecto en el [repositorio xamarin-forms-samples en GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
