Add-Type -AssemblyName PresentationFramework, PresentationCore, WindowsBase, System.Windows.Forms, System.Drawing 
[xml]$xaml =@"
<Window x:Name="MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:local="clr-namespace:WpfApp1"
    Title="MainWindow" Height="450" Width="800">
    <Grid>
        <TextBox
            Name="PrefixTextBox"
            HorizontalAlignment="Left" 
            Height="25"
            Width="120" 
            Margin="10,10,0,0" 
             
            
            Text="Prefix for accounts"
            Foreground="DarkGray"
            VerticalAlignment="Top" 
            TextWrapping="Wrap"
            Padding="0,2,0,0"
        />
        <TextBox 
            HorizontalAlignment="Left"
            Height="25"
            Margin="10,45,0,0"
            VerticalAlignment="Top"
            Width="120"

            TextWrapping="Wrap"
            Text="Hello"
            Padding="0,2,0,0"
        />
        <Button Content="Browse" HorizontalAlignment="Left" Margin="135,10,0,0" VerticalAlignment="Top" Width="120" Height="25"/>
        <Button Content="Browse" HorizontalAlignment="Left" Margin="135,45,0,0" VerticalAlignment="Top" Width="120" Height="25"/>
        <CheckBox Content="CheckBox" HorizontalAlignment="Left" Margin="10,80,0,0" VerticalAlignment="Top"/>
    </Grid>
</Window>
"@

$reader = (New-Object System.Xml.XmlNodeReader $xaml)
$window = [Windows.Markup.XamlReader]::Load($reader)
$PrefixTextBox = $window.FindName("PrefixTextBox")

Function Set-XAMLPlaceHolderText {
    [CmdletBinding(
    )]
    Param(
        [System.Windows.Controls.TextBox]$InputObject,
        [String]$Text
    )
    Begin{
        $InputObject.Text = $Text
        $InputObject.Foreground = "Gray"
    }
    Process{
        $InputObject.Add_GotFocus({
            if ($InputObject.Text -eq $Text){
                $InputObject.Foreground = 'Black'
                $InputObject.Text = ''
            }
        })
    }
    End{
    }
}

Set-XAMLPlaceHolderText -InputObject $PrefixTextBox -Text 'Prefix for accounts'

$null = $window.ShowDialog()
