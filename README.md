# MongoDB Setup

## m - MongoDB Version Manager

`m` helps you download, use, and manage multiple versions of the MongoDB server and command-line tools.

https://github.com/aheckmann/m

To use it we need to install it on docker (or WSL) as we can't directly install it in windows.

### Build the image

> cd aheckmann-SLASH-m

> docker build -t mongo-m .

Now look into the `Docker Desktop` and see in picture you should be able to find `mongo-m` in the image list.

### Run the container with persistent storage

```powershell
docker run -d `
  --name my-mongo `
  -p 27017:27017 `
  -v mongo_data:/data/db `
  mongo-m
```
