# Epic-Seven Team Builder

A team building website that displays various stats, builds, and strategies to play in arena/pvp.

## Getting Started

### Prerequisites

- Docker
- Docker compose
- Nodeenv

### Sample folder structure

```sh
e7-team-builder/
├── README.md
├── e7-backend
├── e7-frontend
└── nenv-e7
```

### Installation/Setup

1. Clone the repo
```sh
git clone https://github.com/tealeaf2/e7-team-builder.git
```

#### Frontend

2. Create a node environment and activate
```sh
nodeenv --node=16.20.2 nenv-e7
source nenv-e7/bin/activate
```

3. Install node packages if not installed
```sh
cd e7-frontend
npm install
```

4. Run project on reload
```sh
nom run dev
```

#### Backend

5. Build docker container and run (optionally) with docker desktop
```sh
cd e7-backend
docker compose -f docker-compose.yml up -d --build
```

6. Create a superuser
```sh
docker compose -f docker-compose.yml run --rm django python manage.py createsuperuser
```

7. Visit http://localhost:8000/admin/ to login to the admin interface