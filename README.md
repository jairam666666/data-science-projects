# IMAGE TO IMAGE TRANSLATION USING CYCLEGAN ARCHITECTURE

The main purpose of project is to transform images from one domain to other domain such as satellite to google maps images etc
This GAN doesnt require paired images unlike pix2pix architecture

Approach:
The model architecture is comprised of two generator models: one generator (Generator-A) for generating images for the first domain (Domain-A) and the second generator (Generator-B) for generating images for the second domain (Domain-B).

    Generator-A -> Domain-A
    Generator-B -> Domain-B

The generator models perform image translation, meaning that the image generation process is conditional on an input image, specifically an image from the other domain. Generator-A takes an image from Domain-B as input and Generator-B takes an image from Domain-A as input.

    Domain-B -> Generator-A -> Domain-A
    Domain-A -> Generator-B -> Domain-B

Each generator has a corresponding discriminator model. The first discriminator model (Discriminator-A) takes real images from Domain-A and generated images from Generator-A and predicts whether they are real or fake. The second discriminator model (Discriminator-B) takes real images from Domain-B and generated images from Generator-B and predicts whether they are real or fake.

    Domain-A -> Discriminator-A -> [Real/Fake]
    Domain-B -> Generator-A -> Discriminator-A -> [Real/Fake]
    Domain-B -> Discriminator-B -> [Real/Fake]
    Domain-A -> Generator-B -> Discriminator-B -> [Real/Fake]

The discriminator and generator models are trained in an adversarial zero-sum process, like normal GAN models. The generators learn to better fool the discriminators and the discriminator learn to better detect fake images. Together, the models find an equilibrium during the training process.

Loss Function:

In addition to the Generator and Discriminator loss, it has one more type of loss called as Cyclic-Consistency loss given by :
