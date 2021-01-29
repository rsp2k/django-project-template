from django.http import HttpResponseNotFound
from django.template import loader
from sentry_sdk import capture_message


def error_404(*args, **kwargs):
    """
    Report 404 errors to Sentry
    """

    # Send to sentry
    capture_message("Page not found!", level="error")
    template = loader.get_template("404.html")

    return HttpResponseNotFound(template.render())