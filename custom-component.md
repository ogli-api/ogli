# Custom Components

When you build a project, `Ogli` creates a `component` folder and adds some files to it. Suppose we have created a `user`
component, then we will see the following files there:

* user_components.py
* test_user_components.py

The `user_components.py` file is where you build your custom components and the `test_user_components.py` is where you 
write the unit tests for the custom components so you'll know if they do what you expect them to do.

## Steps

1. Create a new project: `$ ogli cp customcomponent`

2. Create a new flow: `$ ogli cf transformcar`

3. Test the new flow to make sure everything is working: `$ ogli test transformcar`

4. Make sure the flow generated a file in the ...transformcar-end folder: `$ ogli info`

5. Download it: `$ ogli dl transformcar-end`

To see the fully example check [here](https://docs.ogli.io/building-a-custom-component).