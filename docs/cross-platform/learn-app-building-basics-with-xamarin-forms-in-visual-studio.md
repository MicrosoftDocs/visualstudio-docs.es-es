---
title: Información sobre los conceptos básicos de la compilación de aplicaciones con Xamarin.Forms en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 6c0659e63feb685f002b7be969ee827e5e047cdd
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Información sobre los conceptos básicos de la compilación de aplicaciones con Xamarin.Forms en Visual Studio

Tras realizar los pasos [Setup and install](../cross-platform/setup-and-install.md) y [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md), en este tutorial se muestra cómo compilar una aplicación básica (se muestra a continuación) con Xamarin.Forms. Con Xamarin.Forms, escribirá todo el código de interfaz de usuario una vez en una biblioteca de clases de .NET Standard. Después, Xamarin representará de forma automática los controles de interfaz de usuario nativos para las plataformas iOS, Android y universal de Windows. Se recomienda este enfoque (en lugar de un enfoque compartido) porque la biblioteca de .NET Standard incluye solo esas API de .NET que son compatibles con todas las plataformas de destino, y porque Xamarin.Forms le permite compartir código de interfaz de usuario entre plataformas.  
  
![La aplicación meteorológica de ejemplo en Android, iOS y Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
Deberá llevar a cabo estas operaciones para compilarla:  
  
-   [Configurar la solución](#solution)  
  
-   [Escribir código de servicio de datos compartidos](#dataservice)  
  
-   [Empezar a escribir código de interfaz de usuario compartido](#uicode)  
  
-   [Probar la aplicación mediante el emulador de Visual Studio para Android](#test)  
  
-   [Finalice la interfaz de usuario con una apariencia nativa en todas las plataformas](#finish)  
  
> [!TIP]
> Puede encontrar el código fuente completo para este proyecto en el [repositorio xamarin-forms-samples en GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
##  <a name="solution"></a> Configurar la solución  

En estos pasos, se crea una solución de Xamarin.Forms que contiene una biblioteca de clases de .NET Standard para código compartido y dos paquetes NuGet agregados.  
  
1.  En Visual Studio, cree una nueva solución de **Aplicación multiplataforma (Xamarin.Forms)** con el nombre **WeatherApp**. Busque la plantilla seleccionando **Visual C#** y **Multiplataforma** en la lista de la izquierda.  
  
     Si no la encuentra, es posible que tenga que instalar Xamarin o habilitar la característica de Visual Studio 2017; vea [Configuración e instalación](../cross-platform/setup-and-install.md).  
  
     ![Crear un nuevo proyecto de aplicación en blanco &#40;aplicación de Xamarin.Forms multiplataforma&#41;](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  Después de hacer clic en Aceptar, tendrá la oportunidad de seleccionar determinadas opciones. Elija **Aplicación en blanco**, **Xamarin.Forms** y **.NET Standard**:

     ![Crear un nuevo proyecto de aplicación multiplataforma](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  Después de hacer clic en Aceptar para crear la solución, tendrá un número de proyectos individuales:  
  
    -   **WeatherApp**: la biblioteca de .NET Standard en la que escribirá código que se comparte entre plataformas, incluida la lógica de negocios común y el código de interfaz de usuario con Xamarin.Forms.  
  
    -   **WeatherApp.Android**: el proyecto que contiene el código nativo de Android. Este se establece como el proyecto de inicio predeterminado.  
  
    -   **WeatherApp.iOS**: el proyecto que contiene el código nativo de iOS.  
  
    -   **WeatherApp.UWP**: el proyecto que contiene el código nativo de Windows 10 UWP.  
  
    > [!NOTE]
    >  Puede eliminar cualquiera de los proyectos de una plataforma que no tenga como destino.   
  
     En cada proyecto nativo tiene acceso al diseñador nativo de la plataforma correspondiente y puede implementar pantallas y características específicas de la plataforma según sea necesario.  
  
4.  Actualice el paquete de NuGet Xamarin.Forms en la solución a la última versión estable como sigue. Se recomienda hacerlo siempre que cree una nueva solución de Xamarin:  
  
    -   Seleccione **Herramientas > Administrador de paquetes NuGet > Administrar paquetes NuGet para la solución**.  
  
    -   En la pestaña **Actualizaciones** , active el paquete **Xamarin.Forms** y marque para que se actualicen todos los proyectos de la solución. (Nota: deje las actualizaciones de Xamarin.Android.Support desactivadas).  
  
    -   Actualice el campo **Versión** a la versión **estable más reciente** disponible.  
  
    -   Haga clic en **Instalar**.  
  
         ![Actualización del paquete NuGet Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  
  
5.  Agregue el paquete NuGet **Newtonsoft.Json** al proyecto **WeatherApp**, que usará para procesar la información recuperada de un servicio de datos de tiempo:  
  
    -   En el Administrador de paquetes NuGet (sigue abierto desde el paso 4), seleccione la pestaña **Examinar** y busque **Newtonsoft**.  
  
    -   Seleccione **Newtonsoft.Json**.  
  
    -   Marque el proyecto **WeatherApp** (es el único proyecto en el que debe instalar el paquete).  
  
    -   Asegúrese de que el campo **Versión** está establecido en la versión **estable más reciente** .  
  
    -   Haga clic en **Instalar**.  
  
    ![Localizar e instalar el paquete NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  Repita el paso 5 para buscar e instalar el paquete **Microsoft.Net.Http** .  
  
7.  Compile la solución y compruebe que no hay ningún error de compilación.  
  
##  <a name="dataservice"></a> Escribir código de servicio de datos compartidos  

El proyecto **WeatherApp** es en el que escribirá el código de la biblioteca de .NET Standard que se comparte entre todas las plataformas. La biblioteca se incluye de forma automática en los paquetes de aplicaciones compilados por los proyectos de iOS, Android y Windows.  
  
Para ejecutar este ejemplo, primero debe registrarse para obtener una clave de API gratuita en [http://openweathermap.org/appid](http://openweathermap.org/appid).  
  
En los pasos siguientes se agrega el código a la biblioteca de .NET Standard para tener acceso a los datos de ese servicio meteorológico y almacenarlos:  
  
1.  Haga clic con el botón derecho en el proyecto **WeatherApp** y seleccione **Agregar > Clase...**. En el cuadro de diálogo **Agregar nuevo elemento** , denomine al archivo **Weather.cs**. Esta clase se usará para almacenar los datos del servicio de datos meteorológicos.  
  
2.  Reemplace todo el contenido de **Weather.cs** por lo siguiente:  
  
    ```csharp  
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```  
  
3.  Agregue otra clase al proyecto **WeatherApp** denominada **DataService.cs**, que usará para procesar los datos JSON del servicio de datos meteorológicos.  
  
4.  Reemplace todo el contenido de **DataService.cs** por el código siguiente:  
  
    ```csharp  
    using System.Net.Http;  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
    
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
  
5.  Agregue una tercera clase al proyecto **WeatherApp** denominada **Core**, donde especificará la lógica de negocios compartida. Este código forma una cadena de consulta con un código postal, llama al servicio de datos meteorológicos y luego rellena una instancia de la clase **Weather** .  
  
6.  Reemplace el contenido de **Core.cs** por lo siguiente:  
  
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
  
7.  Compile el proyecto de la biblioteca **WeatherApp** para asegurarse de que el código es correcto.  
  
##  <a name="uicode"></a> Empezar a escribir código de interfaz de usuario compartido  

Xamarin.Forms le permite implementar el código de interfaz de usuario compartido en la biblioteca de .NET Standard. En estos pasos, agregará una página al proyecto con un botón que actualiza su texto con datos que devuelve el código del servicio de datos meteorológicos agregado en la sección anterior:  
  
1.  Agregue una **Página de contenido** denominada **WeatherPage.cs**. Para ello, haga clic con el botón derecho en el proyecto **WeatherApp** y seleccione **Agregar > Nuevo elemento...**. En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Página de contenido**. Tenga cuidado de no seleccionar **Página de contenido (C#)** o **Vista Contenido	**. Asígnele el nombre **WeatherPage.cs**.  
  
     ![Agregar una nueva página XAML de Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     Xamarin.Forms está basado en XAML, por lo que, en este paso, se crea un archivo **WeatherPage.xaml** junto con el archivo de código subyacente anidado **WeatherPage.xaml.cs**. Esto le permite generar la interfaz de usuario mediante código o XAML. Realizará ambos en este tutorial.  
  
2.  Para agregar un botón a la pantalla WeatherPage, reemplace el contenido de **WeatherPage.xaml** por lo siguiente:  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">  
      <Button x:Name="getWeatherBtn" 
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />  
    </ContentPage>  
    ```  
  
     Tenga en cuenta que el nombre del botón debe definirse mediante el atributo **x:Name** para que pueda hacer referencia a este botón por nombre desde el archivo de código subyacente.  
  
3.  Para agregar un controlador de eventos al evento **Clicked** del botón para actualizar el texto del botón, reemplace el contenido de **WeatherPage.xaml.cs** por el código siguiente. (No dude en cambiar "60601" por otro código postal).  
  
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
  
                //Set the default binding to a default object for now  
                BindingContext = new Weather();  
            }  
  
            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
            {  
                Weather weather = await Core.GetWeather("60601");  
                getWeatherBtn.Text = weather.Title;  
            }  
        }  
    }  
    ```  
  
4.  Para abrir **WeatherPage** como la primera pantalla cuando se inicia la aplicación, reemplace el constructor predeterminado en **App.cs** por el código siguiente:  
  
    ```csharp  
    public App()  
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Compile el proyecto **WeatherApp** para asegurarse de que el código es correcto.  
  
##  <a name="test"></a> Probar la aplicación mediante el emulador de Visual Studio para Android  

Ahora ya está listo para ejecutar la aplicación. Vamos a ejecutar solo la versión de Android por ahora para comprobar que la aplicación obtiene datos del servicio meteorológico. Más adelante, también ejecutará las versiones de UWP y iOS después de agregar más elementos de la interfaz de usuario.   
  
1.  Establezca el proyecto **WeatherApp.Android** como el proyecto de inicio; para ello, haga clic en él con el botón derecho y seleccione **Establecer como proyecto de inicio**.  
  
2.  En la barra de herramientas de Visual Studio, verá que **WeatherApp.Android** aparece como el proyecto de destino. Seleccione uno de los emuladores de Android para depurar y pulse **F5**. Se recomienda usar una de las opciones de emulador de **VisualStudio**, que ejecutarán la aplicación en el emulador de Visual Studio para Android.  
  
     ![Seleccionar un destino de depuración del emulador de Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")  
  
3.  Cuando se inicie la aplicación en el emulador, haga clic en el botón **Obtener tiempo** . Debería ver el texto del botón actualizado a **Chicago**, que es la propiedad *Title* de los datos recuperados del servicio meteorológico.  
  
     ![Aplicación meteorológica antes y después de pulsar el botón](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  
  
##  <a name="finish"></a> Finalizar la interfaz de usuario con una apariencia nativa en todas las plataformas  

Xamarin.Forms representa los controles de interfaz de usuario nativos de cada plataforma, para que la aplicación tenga una apariencia nativa de forma automática. Para ver esto de manera más clara, finalizaremos la interfaz de usuario con un campo de entrada para un código postal y, después, se mostrarán los datos meteorológicos que devuelve el servicio.  
  
1.  Reemplace el contenido de **WeatherPage.xaml** por el código siguiente. Se puede hacer referencia a los elementos que se denominan mediante el atributo **x:Name** tal y como se ha descrito anteriormente. Xamarin.Forms también proporciona una serie de [opciones de diseño](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com). En este caso, WeatherPage utiliza [Grid](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) (xamarin.com) y [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
            
                <Label Text="Search by Zip Code" 
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />
            
                <Label x:Name="zipCodeLabel" Text="Zip Code:" 
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />
            
                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />
            
                <Button x:Name="getWeatherBtn" Text="Get Weather" 
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>  
     ```  
  
     Aunque no aparece aquí, puede utilizar la plataforma **OnPlatform** para seleccionar un valor de propiedad que es específico de la plataforma actual en la que se ejecuta la aplicación (vea [External XAML Syntax](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) [Sintaxis XAML externa]) (xamarin.com). En el archivo de código subyacente, puede usar la [API Device.OnPlatform](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) para el mismo propósito.  
  
2.  En **WeatherPage.xaml.cs**, reemplace el controlador de eventos **GetWeatherBtn_Clicked** por el código siguiente. Este código comprueba que hay un código postal en el campo de entrada, recupera datos de ese código postal, establece el contexto de enlace de la página completa para la instancia **Weather** resultante y, después, establece el texto del botón en "Buscar de nuevo". Tenga en cuenta que cada etiqueta de la interfaz de usuario enlaza a una propiedad de la clase **Weather**, así que cuando establece el contexto de enlace de la pantalla en una instancia **Weather**, esas etiquetas se actualizan de manera automática.  
  
    ```csharp  
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
    {  
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
        {  
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
            BindingContext = weather;  
            getWeatherBtn.Text = "Search Again";  
        }  
    }  
    ```  
  
3.  Ejecute la aplicación en las tres plataformas: Android, iOS y Windows. Para ello, haga clic con el botón derecho en el proyecto adecuado, seleccione **Establecer como proyecto de inicio** e inicie la aplicación en un dispositivo, en el emulador o en el simulador. Escriba un código postal de cinco dígitos de Estados Unidos válido (por ejemplo, 60601) y haga clic en el botón **Obtener tiempo** para mostrar los datos meteorológicos de esa región, como se muestra a continuación. Necesitará tener Visual Studio conectado a un equipo Mac OS X en la red para el proyecto de iOS.  
  
     ![La aplicación meteorológica de ejemplo en Android, iOS y Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
Puede encontrar el código fuente completo de este proyecto en el [repositorio xamarin-forms-samples en GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).