# RtlThickness
A simple polyfill for `FlowDirection` aware `Margin` on Xamarin.Forms 3.1

Currently, Xamarin Forms 3.1 has asymmetrical support for `FlowDirection` in Thickness type properties; While `Padding` respects the element's `FlowDirection`, `Margin` does not.
(see [Issue 3066](https://github.com/xamarin/Xamarin.Forms/issues/3066))



## How to use
To use the `FlowDirection` aware `Margin`, just add BiDi.cs to your project and replace all `Margin` to `BiDi.Margin` in XAML.
All the magic happens in [BiDi.cs](https://github.com/danielkatz/RtlThickness/blob/master/RtlThickness/RtlThickness/BiDi.cs).

For example:
```
<ContentView BackgroundColor="Red">
    <ContentView Margin="50,10,100,10" BackgroundColor="White">
        <Label>Margin="50,10,100,10"</Label>
    </ContentView>
</ContentView>
```

Should become:
```
<ContentView BackgroundColor="Red">
    <ContentView local:BiDi.Margin="50,10,100,10" BackgroundColor="White">
        <Label>Margin="50,10,100,10"</Label>
    </ContentView>
</ContentView>
```
Done!

When the issue will be resolved just switch back to the regular `Margin`.
