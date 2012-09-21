bottle-login
============

A login plugin for bottle

    from bottle import run, Bottle 
    from beaker.middleware import SessionMiddleware
    from bottle_login import Plugin
    
    app = Bottle()
    app.install(Plugin(login_url='/login'))
    
    app.route('/login', method=['GET', 'POST'])
    def login():
        if login_success:
            app.login(user)

    @app.get('/')
    def index(user):
        pass

    session_opts = { 
        'session.type': 'file',
        'session.cookie_expires': 3600,
        'session.data_dir': '/tmp',
        'session.auto': True
    }
    app = SessionMiddleware(app, session_opts)

