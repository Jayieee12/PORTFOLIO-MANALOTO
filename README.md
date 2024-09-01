all example will generate


php artisan make:filament-resource User --generate

------------------------------------------------------------
creating an policy for roles user or admin

php artisan make:policy UserPolicy --model=User




xampp
composer
visual studio

laravel new Joel

yes migrate [mysql]

composer require filament/filament:"^3.2" -W

php artisan filament:install --panels 

php artisan make:filament-user

php artisan serve 


php artisan make:filament-resource User

Tables\Columns\TextColumn::make('name')
                    ->searchable(),
                Tables\Columns\TextColumn::make('email')
                    ->searchable(),
                Tables\Columns\TextColumn::make('role')
                    ->searchable(),

  ->schema([
                Forms\Components\TextInput::make('name')
                    ->required(),
                Forms\Components\TextInput::make('email')
                    ->email()
                    ->required(),
                Forms\Components\TextInput::make('password')
                    ->required()
                    ->password()
                    ->revealable(),
                Forms\Components\Select::make('role')
                    ->options(User::ROLES)
                    ->required()
                    ->searchable(),
            ]);

-------------------------------------------------
// adding roles

use Filament\Models\Contracts\FilamentUser;
use Filament\Panel;

class User extends Authenticatable implements FilamentUser

const ROLE_ADMIN = 'ADMIN';

const ROLE_EDITOR = 'EDITOR';

const ROLE_USER = 'USER';

const ROLES = [
    self::ROLE_ADMIN => 'Admin',
    self::ROLE_EDITOR => 'Editor',
    self::ROLE_USER => 'User',
];

public function canAccessPanel(Panel $panel): bool
{
    return $this->can('view-admin',User::class);
}

public function isAdmin(){
    return $this->role === self::ROLE_ADMIN;
}

public function isEditor(){
    return $this->role === self::ROLE_EDITOR;
}


---------------------------------
//database

php artisan make:migrate add_role_to_users

$table->string('role')->default('USER'); // Admin, Editor, User
$table->dropColumn('role');



----------------------------------
//add forfity for allowing roles

composer require laravel/fortify




-----------------------------------
//show image

php artisan storage:link

