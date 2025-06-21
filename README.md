Wan 2.1 & Flux 1.1 Notebook + ComfyUI Workflows

    CPU: Ensure that Google’s provided pc has a GPU (Without it, the notebook won’t work). T4 is the only Free Google’s PC with GPU, it’s slower for generating anything but get’s the work done.

    USE_GOOGLE_DRIVE checkbox: This allows to store data in your drive account, it will be stored in there. It’s recommended to leave unchecked because may cause permission issues, or lack-of-space warnings. These are not critical issues but might obstruct the flow of the installation

Also, models and components are, or too big to store in the free Drive storage provided by Google, or too small to impact installation speed. Anyway, everything is downloaded by Google, so the download speed is very fast.

    UPDATE_COMFY_UI: Updates ComfyUI. Leave checked.

    USE_COMFYUI_MANAGER: Leave this checked. The manager makes easier to install future dependencies, missing nodes or look for new ones.

    INSTALL_CUSTOM_NODES_DEPENDENCIES: Makes what it says. Leave checked.

    WAN/FLUX: The two models. Choose one or Google’s pc will run out of free space in disk and server will not open. (How to change between models will be explained later).

Run:

    The most comfortable way to execute this is in the option upper menu run everything.

    It’s the usual way that I use to run the notebook but sometimes may cause errors due to commands not executing right. Notebooks allow to execute blocks of code and already downloaded files won’t be downloaded again so it may last 1, 2, or 3 seconds to finish, but has to be manually run.

Models/Checkpoints/VAE

    Uncomment (remove only the # in the beginning of the line) and execute the block again to download the desired element. It’s recommended to know what you are downloading and not to uncomment everything as it takes disk space and time.

    Here, custom nodes for both workflows are installed. If more nodes are needed they must be included in it’s own section and with the same format as others.

Run ComfyUI with cloudflared

    Once everything is installed this block will run. After few seconds we will see the CUDA Version, so we ensure that we have a GPU, after that a random link will appear.

    When clicked, another tab will open. Wait 30s and ComfyUI will be set up. When started a window will open to offer to install several models to try them. You can do it, but it will not be explained here, and they are very straightforward to use.

    We close the window and go to the upper left corner Workflow → Open, and we choose the correct workflow. Here we look for the two folders: One for Wan, other for Flux. We choose according to our previous election in the notebook (otherwise models, components and nodes won’t be loaded). In this tutorial we use Flux, so we take that one.

It’s important to know that this tutorial cannot be as exhaustive as we’d like, you can play with/test different options.

    1.	We start by loading the model LOAD DIFFUSION MODEL, we use Flux1-dev-fp8.safetensors and weighted with fp8_[anything]. You can use any fp8 option to test and chose the best combinations, but ensure that the weights match the model.
    2.	DUALCLIPLOADER, here we set the clips that we will use, type flux and device cpu.
    3.	LOAD VAE, ensure to load the Flux ones. Anyway, if you choose another an error will popup, nothing more.
    4.	BASICSCHEDULER, it’s a good practice to look for the best combination between the scheduler and the sampler (In KSAMPLESELECT node). The steps are the number of iterations that the model will do before finish.

We click in run and wait, then we will have our image.

To change model/Erase data

    We close ComfyUI and go to the Notebook, as we did before: Runtime → Change runtime type, then we choose another one. When it sais that the machine is connected, we come back to our previous machine (or another, but ensure to have GPU).

    Now we choose Wan/Flux, uncheck the other model and click Runtime → Run All. Everything will start downloading again.

Troubleshoot

    Once everything is set up, if we try to open the link and an error occurs, like „Server not found“: Stop the last block of code and start it again.

    We repeat the process: Open the correct folder with workflows and load it.

    The previous explanation applies to these nodes, and most of the attributes can be changed with double click or just dragging.






