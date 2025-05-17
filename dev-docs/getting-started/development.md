---
icon: square-terminal
---

# Development

| <p><a href="https://github.com/voxel51/fiftyone"><img src="_static/images/icons/github-logo-256px.png" alt="GitHub repository"><br>  View on GitHub</a></p> | <p><a href="https://community.voxel51.com/"><img src="_static/images/icons/discord-logo-256px.png" alt="Discord community"><br>  Join us on Discord</a></p> | <p><a href="https://colab.research.google.com/github/voxel51/fiftyone-examples/blob/master/examples/quickstart.ipynb"><img src="_static/images/icons/colab-logo-256px.png" alt="Colab quickstart"><br>  Try it in Colab</a></p> |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

**The open-source tool for building high-quality datasets and computer vision models**

Nothing hinders the success of machine learning systems more than poor quality\
data. And without the right tools, improving a model can be time-consuming and\
inefficient.

FiftyOne supercharges your machine learning workflows by enabling you to\
visualize datasets and interpret models faster and more effectively.

<figure><img src="../.gitbook/assets/02_04_25_add_api_spec.svg" alt=""><figcaption></figcaption></figure>

Improving data quality and understanding your model's failure modes are the\
most impactful ways to boost the performance of your model.

FiftyOne provides the building blocks for optimizing your dataset analysis\
pipeline. Use it to get hands-on with your data, including visualizing complex\
labels, evaluating your models, exploring scenarios of interest, identifying\
failure modes, finding annotation mistakes, and much more!

<a href="../integrations/contentkit/interactivity.md" class="button primary">Install FiftyOne!</a>

FiftyOne integrates naturally with your favorite tools. Click on a logo to learn how:

{% hint style="info" %}
**Note:**

FiftyOne is growing\![Sign up for the mailing list](https://share.hsforms.com/1zpJ60ggaQtOoVeBqIZdaaA2ykyk)\
to learn about new features as they come out.
{% endhint %}

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><h4>Curating datasets</h4></td><td>Surveys show that machine learning engineers spend over half of their time wrangling data, but it doesn't have to be that way. Use FiftyOne's powerful dataset import and manipulation capabilities to manage your data with ease.</td><td><a href="../.gitbook/assets/02_04_25_add_api_spec.svg">02_04_25_add_api_spec.svg</a></td></tr></tbody></table>

**Core Capabilities**

.. customcalloutitem::\
:header: Visualizing embeddings\
:description: Are you using embeddings to analyze your data and models? Use FiftyOne's embeddings visualization capabilities to reveal hidden structure in you data, mine hard samples, pre-annotate data, recommend new samples for annotation, and more.\
:button\_text: Experience the power of embeddings\
:button\_link: tutorials/image\_embeddings.html\
:image: \_static/images/homepage\_embeddings.gif

.. customcalloutitem::\
:header: Working with geolocation\
:description: Many datasets have location metadata, but visualizing location-based datasets has traditionally required closed source or cloud-based tools. FiftyOne provides native support for storing, visualizing, and querying datasets by location.\
:button\_text: Visualize your location data\
:button\_link: user\_guide/plots.html#geolocation-plots\
:image: \_static/images/homepage\_location.gif

.. customcalloutitem::\
:header: Finding annotation mistakes\
:description: Annotations mistakes create an artificial ceiling on the performance of your model. However, finding these mistakes by hand is not feasible! Use FiftyOne to automatically identify possible label mistakes in your datasets.\
:button\_text: Check out the label mistakes tutorial\
:button\_link: tutorials/classification\_mistakes.html\
:image: \_static/images/homepage\_mistakes.gif

.. customcalloutitem::\
:header: Removing redundant images\
:description: During model training, the best results will be seen when training on unique data. Use FiftyOne to automatically remove duplicate or near-duplicate images from your datasets and curate diverse training datasets from your raw data.\
:button\_text: Try the image uniqueness tutorial\
:button\_link: tutorials/uniqueness.html\
:image: \_static/images/homepage\_redundant.gif

.. End callouts ---------------------------------------------------------------

.. raw:: html

```
    </div>
</div>
```

.. End of callout items -------------------------------------------------------

**Core Concepts**

.. \_fiftyone-library:

## FiftyOne Library

FiftyOne's core library provides a structured yet dynamic representation to\
explore your datasets. You can efficiently query and manipulate your dataset by\
adding custom tags, model predictions and more.

.. custombutton::\
:button\_text: Explore the library\
:button\_link: user\_guide/basics.html

```python
:linenos:
import fiftyone as fo
dataset = fo.Dataset("my_dataset")
sample = fo.Sample(filepath="/path/to/image.png")
sample.tags.append("train")
sample["custom_field"] = 51
dataset.add_sample(sample)
view = dataset.match_tags("train").sort_by("custom_field").limit(10)
for sample in view:
print(sample)
```

> **Note:** FiftyOne is designed to be lightweight and flexible, making it easy to load\
> your datasets. FiftyOne supports loading datasets in a variety of common\
> formats out-of-the-box, and it also provides the extensibility to load\
> datasets in custom formats.

```
Check out :doc:`loading datasets <user_guide/dataset_creation/index>` to see
how to load your data into FiftyOne.
```

## FiftyOne App

The FiftyOne App is a graphical user interface that makes it easy to explore\
and rapidly gain intuition into your datasets. You can visualize labels like\
bounding boxes and segmentations overlaid on the samples; sort, query and\
slice your dataset into any subset of interest; and more.

.. custombutton::\
:button\_text: See more of the App\
:button\_link: user\_guide/app.html

![fiftyone-app](images/homepage_app.png)

## FiftyOne Brain

The FiftyOne Brain is a library of powerful machine learning-powered\
capabilities that provide insights into your datasets and recommend ways to\
modify your datasets that will lead to measurably better performance of your\
models.

.. custombutton::\
:button\_text: Learn more about the Brain\
:button\_link: brain.html

```python
:linenos:
import fiftyone.brain as fob
fob.compute_uniqueness(dataset)
rank_view = dataset.sort_by("uniqueness")
```

## FiftyOne Plugins

FiftyOne provides a powerful plugin framework that allows for extending and\
customizing the functionality of the tool to suit your specific needs.

With plugins, you can add new functionality to the FiftyOne App, create\
integrations with other tools and APIs, render custom panels, and add custom\
buttons to menus.

With :ref:`FiftyOne Enterprise <enterprise-delegated-operations>`, you can even write\
plugins that allow users to execute long-running tasks from within the App that\
run on a connected compute cluster.

.. custombutton::\
:button\_text: Install some plugins!\
:button\_link: plugins/index.html

![fiftyone-plugins](images/plugins/operators/examples/embeddings.gif)

## Dataset Zoo

The FiftyOne Dataset Zoo provides a powerful interface for downloading datasets\
and loading them into FiftyOne.

It provides native access to dozens of popular benchmark datasets, and it als\
supports downloading arbitrary public or private datasets whose\
download/preparation methods are provided via GitHub repositories or URLs.

.. custombutton::\
:button\_text: Check out the Dataset Zoo\
:button\_link: dataset\_zoo/index.html

```python
:linenos:
import fiftyone as fo
import fiftyone.zoo as foz
dataset = foz.load_zoo_dataset("coco-2017", split="validation")
session = fo.launch_app(dataset)
```

![dataset-zoo](images/dataset_zoo_coco_2017.png)

## Model Zoo

The FiftyOne Model Zoo provides a powerful interface for downloading models and\
applying them to your FiftyOne datasets.

It provides native access to hundreds of pre-trained models, and it also\
supports downloading arbitrary public or private models whose definitions are\
provided via GitHub repositories or URLs.

.. custombutton::\
:button\_text: Check out the Model Zoo\
:button\_link: model\_zoo/index.html

```python
:linenos:
import fiftyone as fo
import fiftyone.zoo as foz
dataset = foz.load_zoo_dataset(
"coco-2017",
split="validation",
max_samples=50,
shuffle=True,
)
model = foz.load_zoo_model(
"clip-vit-base32-torch",
text_prompt="A photo of a",
classes=["person", "dog", "cat", "bird", "car", "tree", "chair"],
)
dataset.apply_model(model, label_field="zero_shot_predictions")
session = fo.launch_app(dataset)
```

**What's Next?**

Where should you go from here? You could...

* :ref:`Install FiftyOne <installing-fiftyone>`
* Try one of the :doc:`tutorials <tutorials/index>` that demonstrate the unique\
  capabilities of FiftyOne
* Explore :doc:`recipes <recipes/index>` for integrating FiftyOne into\
  your current ML workflows
* Check out the :doc:`cheat sheets <cheat_sheets/index>` for topics you may\
  want to master quickly
* Consult the :doc:`user guide <user_guide/index>` for detailed instructions on\
  how to accomplish various tasks with FiftyOne

**Need Support?**

If you run into any issues with FiftyOne or have any burning questions, feel\
free to [connect with us on Discord](https://community.voxel51.com) or reach out to\
us at support@voxel51.com.

.. toctree::\
:maxdepth: 1\
:hidden:

Overview FiftyOne Enterprise 🚀 \<enterprise/index>\
Installation \<getting\_started/install>\
Environments \<environments/index>\
Tutorials \<tutorials/index>\
Recipes \<recipes/index>\
Cheat Sheets \<cheat\_sheets/index>\
User Guide \<user\_guide/index>\
Dataset Zoo \<dataset\_zoo/index>\
Model Zoo \<model\_zoo/index>\
FiftyOne Brain Integrations \<integrations/index>\
Plugins \<plugins/index>\
CLI \<cli/index>\
API Reference \<api/fiftyone>\
Release Notes Deprecation Notices FAQ \<faq/index>
