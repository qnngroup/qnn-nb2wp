# Parser for Uploading Jupyter Notebooks to the QNN Blog

This tool parses Jupyter notebooks for posting to the QNN blog.  It is based off of the work from [this repository](https://github.com/bennylp/nb2wp).

## Usage for posting to the QNN Blog

There are two steps:

 1. Use qnn_nb2wp to convert the Jupyter notebook to html and separate image files.
 2. Upload the html and image files as a QNN blog post.

### Step 1: HTML and Image Conversion

For a minimal html conversion simply follow these steps:

 1. Download `qnn_nb2wp.py` as well as `style.css` from the QNN Github [here](https://github.com/qnngroup/qnn-nb2wp/tree/main) and put them into the same folder as your Jupyter notebook
 2. In python run the following code with the `img_prefix` variable being the prefix of the image filenames and `img_url_prefix` being the prefix to the media directory of the blog post on the QNN blog (something like `https://qnn.mit.edu/wordpress/wp-content/uploads/2024/08/`
    
```
from qnn_nb2wp import *
qnn_nb2wp('name_of_notebook.ipynb', img_prefix='prefix', img_url_previx='url-prefix')
```

This results in a folder of the same name as the `.ipynb` file with an html file and a directory of exported images.  Next we will tackle posting this to the blog.

### Step 2: Upload to the QNN Blog

After the export tool has run, you now just need to export the html output to the blog.  To do this:

 1. Create a new post
 2. Go to Text edit mode
 3. Copy and paste the html text output into the text edit window of the WordPress post
 4. Upload all images to the media folder of the blog
 
Now you should be able to preview and post the blog as usual.  Done!

## Changes to the original code

The following changes have been made to update the code from the [original tool](https://github.com/qnngroup/qnn-nb2wp/tree/main).

1. The nbconvert commands around the HTML template name specification were updated to the new syntax (this was changed from the original version).
2. A new `img_prefix` input was added to specify the image prefix name to prevent naming conflicts on the QNN blog media folder.
