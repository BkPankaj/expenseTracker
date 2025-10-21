FROM --platform=linux/amd64 python:3.11.4
WORKDIR /app

# Copy the distribution package
COPY dist/dsservice-0.1.0.tar.gz .

# Install the distribution package
RUN pip install --no-cache-dir dsservice-0.1.0.tar.gz

RUN pip uninstall -y langchain-core langchain-google-genai && \
    pip install langchain-core==0.3.74 langchain-google-genai==2.1.9 python-dotenv==1.0.1

# Set the environment variable for the Flask app
ENV FLASK_APP=src/app/__init__.py

# Expose the port
EXPOSE 8010

# Start the Flask app
CMD ["flask", "run", "--host=0.0.0.0", "--port=8010"]