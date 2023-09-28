# rails new postulaciones -d postgresql cd postulaciones
# configuracion de base de datos 
  rails db:create
# agregar gemas 
  bundle add devise
  bundle add faker
  bundle add figaro
  bundle exec figaro install
en config/application.yml 
  agregar :
  # Database configuration
  DATABASE_URL: "postgres://username:password@localhost/postulaciones_development"
  # AWS S3 configuration for image storage
  AWS_ACCESS_KEY_ID: "your_access_key_id"
  AWS_SECRET_ACCESS_KEY: "your_secret_access_key"
  AWS_REGION: "your_aws_region"
  AWS_BUCKET: "your_s3_bucket"
# configurar devise 
rails generate devise:install
rails generate devise User


# Generar el modelo User
rails generate model User name:string email:string password_digest:string is_admin:boolean
# Generar el modelo JobOffer
rails generate model JobOffer title:string description:text is_published:boolean
# Generar el modelo Application
rails generate model Application user:references job_offer:references
