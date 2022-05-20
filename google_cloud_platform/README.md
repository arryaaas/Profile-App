# Documentation

Task:

1. Deploy Profile App on **Google Compute Engine (GCE)** or **Google App Engine (GAE)**.
2. The Profile App must display an image retrieved from **Google Cloud Storage (GCS)**.

## Enable Cloud Build API

1. In the Cloud Console, go to the **Navigation Menu** > **APIs & Services** > **Library**.
2. Type **Cloud Build API** in search box.
3. Click **Cloud Build API**.
4. Click **Enable**.

## Download the Profile App

1. Copy the Profile App repository to Google Cloud instance.

    ```
    git clone https://github.com/arryaaas/Profile-App.git
    ```

2. Open app directory.

    ```
    cd Profile-App
    ```

## Creating a Cloud Storage Bucket

1. Make a bucket.

    ```
    gsutil mb -l asia-southeast2 gs://profile-app
    ```

2. See a list of existing buckets in the project.

    ```
    gsutil ls
    ```

## Uploading an Object to a Bucket

1. Open images directory.

    ```
    cd images
    ```

2. Upload `favicon.ico` and `profile.png` to bucket.

    ```
    gsutil cp favicon.ico gs://profile-app

    gsutil cp profile.png gs://profile-app
    ```

3. Seee a list of objects stored in the bucket.

    ```
    gsutil ls gs://profile-app
    ```

4. Added read permission for `favicon.ico` and `profile.png`.

    ```
    gsutil acl ch -u AllUsers:R gs://profile-app/favicon.ico

    gsutil acl ch -u AllUsers:R gs://profile-app/profile.png
    ```

5. Open app directory.

    ```
    cd ..
    ```

## Make a change

1. In **Cloud Shell** click **Open editor**.
2. Open `app/templates/index.html`.
3. Change `FAVICON_URL` to **Public URL** of favicon.ico.
4. Change `PROFILE_URL` to **Public URL** of profile.png.
5. Save the file.

## Test the app

1. Start the Google Cloud development server.

    ```
    python main.py
    ```

2. In **Cloud Shell** click **Web preview** > **Preview on port 8080**.
3. To stop the Google Cloud development server, press **Ctrl+C** on the **Cloud Shell**.

## Creating a App Engine

1. In the Cloud Console, go to the **Navigation menu** > **App Engine**.
2. Click **Create Application**.
3. Select **asia-southeast2** as **Region**.
4. Click **Create App**.
5. Set the following values, leave all other values at their defaults:

    | Property    | Value (type value or select option as specified) |
    | ----------- | ------------------------------------------------ |
    | Language    | Python                                           |
    | Environment | Standard                                         |

6. Click **Next**.
7. Click **I’ll do this later**.

## Deploy the app

1. Deploy the app to App Engine. Make sure you are in the app folder.

    ```
    gcloud app deploy
    ```

2. Enter **Y** when prompted to confirm the details and begin the deployment of service.

## View the app

1. Launch the browser.

    ```
    gcloud app browse
    ```

2. Click on the link it provides.
